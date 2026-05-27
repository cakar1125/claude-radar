# [2026-05-27] Claude Radar

## Bu Dönemde Yenilikler

### Code with Claude 2026 Etkinliği (6 Mayıs) — Önceki Raporda Eksik Kalanlar

Anthropic'in San Francisco, Londra ve Tokyo'da düzenlediği geliştirici konferansı 5 büyük özellik getirdi. Yeni model duyurusu yoktu; odak noktası production-ready agent altyapısına kaydı.

- **Dreaming** (research preview) — Agent'lar artık session'lar arasında kendi geçmişlerini inceliyor, hatalarını analiz ediyor ve belleğini otomatik olarak iyileştiriyor. Ekip tercihleri, tekrar eden hatalar ve ideal workflow'lar otomatik öğreniliyor. Kontrolü kullanıcı belirliyor: otomatik güncelleme veya manuel onay.
- **Outcomes** (public beta) — Başarı kriterini bir rubric olarak yazıyorsun, agent hedefler. Ayrı bir "grader agent" task'ı bağımsız değerlendiriyor. Anthropic'in testlerinde %10,1 kalite artışı sağlandı.
- **Claude Finance** — 10 hazır finansal agent paketi: pitch builder, market researcher, month-end closer vb.
- **Add-ins** — Claude artık Word gibi uygulamaların içinde doğal çalışıyor; harici API yerine yazılımın kendi context'ini anlıyor.
- **SpaceX compute ortaklığı + Claude Code limitleri 2x artış** — 5 saatlik session limitleri ikiye katlandı.

### Claude Code Güncellemeleri (19-27 Mayıs)

- **v2.1.147 (22 Mayıs):** `/simplify` komutu `/code-review` olarak yeniden adlandırıldı, çaba seviyesi raporlaması eklendi. Pinned background session'lar artık boşta kalınca kapanmıyor; güncellemeler için otomatik yeniden başlıyor.
- **v2.1.149 (23 Mayıs):** `/usage` komutu artık skills, subagent'lar, plugin'ler ve MCP server maliyetlerini kategoriye göre ayrıştırarak gösteriyor. Diff görünümünde klavye navigasyonu (ok tuşları, j/k, Space, Home/End). Markdown task list'leri GFM checkbox formatıyla render ediliyor (- [ ] / - [x]). PowerShell güvenlik açıkları ve sandbox vulnerability'leri kapatıldı.

### Platform Haberleri

- **Stainless Satın Alması (18 Mayıs)** — Anthropic, SDK üretim platformu Stainless'ı satın aldı. Claude API SDK'larının (Python, TypeScript, Go, Java, PHP, C#, Ruby) kalitesi uzun vadede artacak.
- **KPMG Entegrasyonu (19 Mayıs)** — 276.000 kişilik iş gücü genelinde Claude enterprise entegrasyonu.
- **Web Search → Zengin SEC Verileri (18 Mayıs)** — Web search tool artık SEC dosyalarından daha zengin finansal veri döndürüyor. Rakip şirket / publisher araştırması için kullanışlı.

### Project Glasswing Güncellemesi (22 Mayıs)

**Claude Mythos** model preview, 1.000+ açık kaynak projede 23.019 güvenlik açığı tespit etti; 6.202'si yüksek/kritik seviyede. SWE-Bench: %93,9 (mevcut en yüksek). Savunma amaçlı siber güvenlik odaklı; genel kullanıma açılması planlanmıyor.

---

## Indie Oyun Geliştirici İçin Bu Haftanın En İyi 3 Kullanımı

### 1. Dreaming ile Kendini Öğreten Oyun Geliştirme Agent'ı
**Ne Yapıyor:** Claude Managed Agents üzerinde Dreaming aktifleştirildiğinde, agent proje boyunca yaptığı her session'dan öğreniyor. Birkaç session sonra kendi GDScript tercihlerini, mimari kararlarını ve yaygın hatalarını öğreniyor.

**Nasıl:**
1. `ant` CLI veya Managed Agents API ile bir Godot geliştirme agent'ı kur
2. İlk session'da proje yapını, kod stilini ve kurallarını anlat
3. Dreaming'i aktif et (managed-agents-2026-04-01 beta header gerekli)
4. Her geliştirme session'ından sonra agent hafızasını otomatik kürase ediyor
5. 5-6 session sonra agent sana naming convention'ları sormuyor, direkt uygulayabiliyor

**Örnek Prompt:**
```
Bu proje bir Godot 4 roguelite. Mimari kurallarım:
- Tüm entity'ler res://entities/ altında
- State machine: StateMachine.gd base class
- Sinyal adlandırma: on_[nesne]_[eylem] (on_player_died, on_enemy_spawned)
- Her sistem kendi autoload'u (GameManager, AudioManager, EventBus)
- GDScript, C# yok
Bu oturumda bu kuralları öğren ve bir dungeon entity sistemi yaz.
```
**Beklenen Çıktı:** İlk session kuralları öğrenir; sonraki session'larda otomatik uygular, artık her seferinde açıklaman gerekmez.

---

### 2. Outcomes ile "Bitti mi?" Kriterli Seviye Tasarımı
**Ne Yapıyor:** Bir seviyenin veya sistemin "tamamlanma" kriteri tanımlanıyor; ayrı bir grader agent kodu inceleyip kriterleri geçip geçmediğine karar veriyor. Subjektif "yeterince iyi" kararını otomatize ediyor.

**Nasıl:**
1. Managed Agents ile bir level generation session'ı aç
2. Outcome rubric'ini tanımla
3. Claude kodu yazar, grader bağımsız olarak değerlendirir, geçene kadar iterate eder

**Örnek Outcome Rubric:**
```
BAŞARI KRİTERLERİ:
1. Her oda en az 1 çıkış noktasına sahip olmalı (dead end yok)
2. Başlangıç ile bitiş odası arasında çözülebilir bir yol bulunmalı
3. Minimum 8, maksimum 16 oda üretilmeli
4. Hiçbir oda başka bir oda ile üst üste gelmemeli
5. En az 1 boss odası ve 2 hazine odası içermeli

GRADER: Her kriteri pass/fail olarak değerlendir.
Tümü pass ise: TAMAMLANDI. Herhangi biri fail ise: başarısız kriterleri listele.
```
**Beklenen Çıktı:** Agent kriterler geçene kadar kendi başına iterate eder; sen sadece sonucu onaylarsın.

---

### 3. /code-review ile Oyun Kodu Kalite Kontrolü
**Ne Yapıyor:** Eskiden `/simplify` olan komut, `/code-review` olarak yeniden adlandırıldı ve çaba seviyesi raporlaması eklendi. Oyun sistemini hızla review ettirip performans sorunlarını, anti-pattern'leri yakalatabilirsin.

**Nasıl:**
1. Claude Code'da oyun sistemi kodunu aç
2. `/code-review` komutunu çalıştır (çaba seviyesi seçeneği: low/medium/high)
3. Diff görünümünde ok tuşlarıyla veya j/k ile bulgular arasında gezin

**Örnek Prompt (review'dan önce bağlam ver):**
```
Bu GDScript dosyası bir enemy AI state machine.
60 FPS altına düşüyor, özellikle 20+ enemy spawn olunca.
/code-review → high effort ile:
1. _process() içinde gereksiz her kare çalışan hesaplamaları bul
2. Sinyal bağlantılarının doğru temizlenip temizlenmediğini kontrol et
3. Godot 4 idiomlarına aykırı pattern'leri işaretle
```
**Beklenen Çıktı:** Kategorize edilmiş bulgular listesi + performans darboğazları + önerilen düzeltmeler.

---

## Bu Haftanın Önerilen Workflow'u

**"Öğrenen Agent Stüdyosu" — Dreaming + Outcomes Kombinasyonu:**

```
Hafta 1 (Kurulum):
→ Managed Agent kur, proje kurallarını öğret
→ Dreaming aktif et
→ Her gün 1-2 küçük görev session'ı yap

Hafta 2+:
→ Agent artık proje kurallarını içselleştirmiş
→ Büyük görevler için Outcomes rubric'i tanımla
→ Agent kriter geçene kadar kendi başına iterate eder

Sen sadece:
→ Sanat/ses/tasarım kararları
→ Büyük mimari yön belirleme
→ Outcomes rubric'ini yazmak
```

---

## Gizli Kalmış İpucu

**`/usage` Kategorik Maliyet Takibi (v2.1.149)**

Yeni `/usage` komutu artık sadece token sayısını değil, kullanımı kategoriye göre ayırarak gösteriyor: skills, subagent'lar, plugin'ler, MCP server maliyetleri. Solo indie dev için hangi workflow adımının maliyetli olduğunu görmek demek. Örnek: MCP server çağrıları pahalıysa, o işlemi Agent Skills'e taşıyabilirsin.

```
/usage
→ Skill invocations: X tokens
→ Subagent calls: Y tokens
→ MCP tool calls: Z tokens
→ Estimated session cost: $X.XX
```

---

## Önceki Tahminlerin Doğrulanması

| Tahmin (25 Mayıs) | Durum |
|---|---|
| Sonnet 4 + Opus 4 retirement 15 Haziran 2026 | ⏳ Yaklaşıyor — 19 gün kaldı |
| Multiagent Orchestration GA | ⏳ Hâlâ public beta'da |
| MCP Tunnels yaygınlaşması | ✅ Research Preview olarak 19 Mayıs'ta çıktı |
| Claude Design (labs'ten çıkış) | ❓ Henüz belirsiz |
| GameMaker GMRT olgunlaşması | ⏳ Q3 2026 beklentisi devam ediyor |

---

## Yakında Gelebilecekler

- **15 Haziran 2026 — Claude Sonnet 4 + Opus 4 emekliye ayrılıyor.** 19 gün kaldı. Bu modelleri kullanan tüm pipeline'lar için geçiş zorunlu.
- **Dreaming GA:** Şu an research preview; public beta ve GA yol haritasında. Indie dev agent'larının "kendi kendine öğrenmesi" için API erişimi bekleniyor.
- **Add-ins genişlemesi:** Şimdilik Word/Office; oyun engine IDE
'lerine (Godot plugin, GameMaker uzantisi) benzer entegrasyonlar topluluktan gelmeye baslayabilir.
- **Claude Mythos etkileri:** Guvenlik odakli Mythos preview yetenekleri (SWE-Bench %93,9) ozellik seviyesinde ana modellere yansiyabilir.
- **Stainless etkisi:** SDK kalitesi - ozellikle TypeScript ve Python - onumuzdeki 1-2 ay icinde iyilesmeye baslayacak.
