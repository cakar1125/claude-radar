# [2026-05-25] Claude Radar

## Bu Dönemde Yenilikler

### Model Güncellemeleri
- **Claude Opus 4.7** (16 Nisan 2026) — SWE-Bench'de %87.6 (Opus 4.6'dan +13 puan), 3x daha yüksek çözünürlüklü görsel input, aynı fiyat ($5/$25 per MTok). API breaking changes var — geçmeden önce migration guide oku.
- **Fast Mode Opus 4.7 desteği** (12 Mayıs 2026) — `speed: "fast"` ile 2.5x daha hızlı output.

### Claude Platform / API (Nisan-Mayıs 2026)
- **Agent Memory public beta** (23 Nisan 2026) — Agentlar geçmiş oturumları analiz edip kendi kendini geliştiriyor ("Dreaming" özelliği)
- **Multiagent Orchestration public beta** (6 Mayıs 2026) — Baş agent işi parçalara bölerek parallel uzman agentlara devrediyor, shared filesystem üzerinden koordinasyon
- **MCP Tunnels Research Preview** (19 Mayıs 2026) — Private network içindeki MCP serverlarına public internet olmadan erişim
- **Self-hosted Sandboxes** (19 Mayıs 2026) — Anthropic altyapısı yerine kendi sunucunda çalışan sandbox
- **Cache Diagnostics public beta** (13 Mayıs 2026) — `cache_miss_reason` ile prompt cache'inin neden atlandığını görebiliyorsun
- **Advisor Tool public beta** (9 Nisan 2026) — Hızlı executor model + zeki advisor model kombinasyonu; uzun agentic işlerde kalite/maliyet dengesi
- **Claude Platform on AWS** (11 Mayıs 2026) — Tam Messages API, IAM auth ile AWS üzerinden
- **`ant` CLI** (8 Nisan 2026) — Claude API için yeni komut satırı client, YAML ile API kaynakları
- **Claude Managed Agents** GA public beta (8 Nisan 2026) — Tam yönetilen agent altyapısı, güvenli sandboxing, streaming

### Claude Code
- **Agent View** — `claude agents` komutu ile tek ekrandan tüm session'ları yönet; peek panel ile bloke olan session'a direkt cevap ver
- **Background Sessions `/bg`** — `/resume` ile background session'ları interactive session'larla aynı listede görüyorsun, süre gösteriyor
- **Desktop App Plugin Parity** — CLI'da çalışan pluginler desktop app'te de aynen çalışıyor
- **SSH Support on Mac** — Artık Linux'a ek olarak Mac'te de SSH session desteği
- **/mcp tool count** — `/mcp` komutu bağlı serverdaki tool sayısını gösteriyor
- **--plugin-dir .zip desteği** — Plugin dizinlerine ek olarak .zip arşivleri de kabul ediliyor

### Oyun Geliştirme Haberleri
- **GameMaker GMRT + Claude Code entegrasyonu** (30 Nisan 2026) — Editör içinden doğal dil ile AI destekli geliştirme
- **Claude Code Game Studios** — 49 agent, 73 skill ile açık kaynak sanal stüdyo yapısı (GitHub'da mevcut)
- **2026 Unity Raporu:** Dünya genelinde oyun stüdyolarının %95'i AI'yı core workflow'a entegre etmiş

---

## Indie Oyun Geliştirici İçin Bu Haftanın En İyi 3 Kullanımı

### 1. Paralel Agent ile Eş Zamanlı Geliştirme (Agent View)
**Ne Yapıyor:** Birden fazla Claude Code session'ını aynı anda çalıştırarak farklı görevleri paralel yürütür — biri kod yazarken diğeri başka bir sistem üzerinde çalışır.

**Nasıl:**
1. Terminal'de `claude agents` yaz → Agent View açılır
2. `N` ile yeni session başlat, isim ver (örn. "pcg-system", "ui-builder")
3. Uzun işi başlat → `/bg` ile arka plana at
4. Başka bir session aç, orada çalış
5. Arka plandaki session soru sorarsa bildirim gelir → Space ile peek panel aç, cevap ver

**Örnek Prompt:**
```
Sen bir Godot 4 indie oyununda procedural dungeon generation sistemi yazıyorsun.
Çalışma dizini: res://scripts/world/
Görev: DungeonGenerator.gd oluştur.
- BSP algoritması ile 10-15 oda üret
- Koridorlarla bağla
- Her odaya rastgele chest/enemy spawn noktası ekle
- TileMapLayer kullan
Bitince çalıştırma komutunu ver.
```
**Beklenen Çıktı:** Hazır DungeonGenerator.gd dosyası + test talimatı; sen bu sırada başka session'da çalışabilirsin.

---

### 2. GameMaker GMRT ile Doğal Dil Kod Yazımı
**Ne Yapıyor:** GameMaker'ın yeni Claude Code entegrasyonuyla editör içinden doğrudan Claude'a görev verip kodu otomatik entegre etme.

**Nasıl:**
1. GameMaker GMRT'de Claude Code entegrasyonunu aktif et (Settings → AI Integration)
2. İstediğin object'e sağ tıkla → "Ask Claude"
3. Görevi Türkçe veya İngilizce anlat
4. Claude kodu yazar ve proje dosyalarına bağlar

**Örnek Prompt:**
```
Bu düşman object için:
- Oyuncu 200px yakına gelince chase başlasın
- HP sıfırlanınca obj_coin'den rastgele 1-3 adet spawn etsin
- Hasar alınca kırmızıya 0.1 sn flash yapsın
State machine kullan. GML ile yaz.
```
**Beklenen Çıktı:** Doğrudan GameMaker projesine entegre edilmiş çalışır GML kodu.

---

### 3. Lore-Aware NPC Diyalog Üreteci (Prompt Caching ile)
**Ne Yapıyor:** Oyunun tüm lore'unu bir kere cache'leyerek her NPC sahnesi için sadece küçük bir değişken prompt gönderir; maliyet %90'a kadar düşer.

**Nasıl:**
1. Oyunun lore'unu bir LORE.md dosyasına yaz (bir kere)
2. İlk promptta lore'u ver ve `cache_control` ekle
3. Her NPC sahnesi için sadece NPC profili + oyuncu durumu değişir

**Örnek Prompt:**
```
[LORE.md içeriği — sadece ilk seferinde tam ver, sonraki çağrılarda cache'lenir]

---
Şimdi bu sahneyi yaz:
NPC: Yaşlı demirci Gareth, 60 yaşında, oğlunu ejderhaya kaybetti.
Durum: Oyuncu o ejderhayı öldürdü ve silahını satmak için geldi.
Oyuncu eşyası: Dragon Fang Sword

Üret:
1. Gareth'in iç düşüncesi (1 paragraf)
2. 3 diyalog seçeneği (agresif / nötr / empatik)
3. Her seçenek için Gareth tepkisi + quest trigger
4. Sonraki sahneler için Gareth'in hafıza notları
```
**Beklenen Çıktı:** Lore'la tutarlı, duygusal derinliği olan diyalog ağacı + persistent hafıza notları.

---

## Bu Haftanın Önerilen Workflow'u

**"Sabah Planla, Claude Üretsin" — Indie Solo Dev Döngüsü:**

```
Sabah (15 dk):
→ Günün görevlerini Claude'a ver
→ Claude önceliklendirsin + süre tahmini yapsın
→ Uzun işleri Agent View arka planına at

Gün boyunca:
→ Sen sanat/tasarım/test yaparken Claude arka planda kod üretiyor
→ Bildirim gelince peek panel'de yönlendir veya onayla

Akşam (30 dk):
→ Üretilen kodu gözden geçir
→ "Bu günün retrospektifi" promptu ile neyin işe yaramadığını analiz ettir
→ Ertesi gün için context dosyasını güncelle
```

---

## Gizli Kalmış İpucu

**Advisor Tool: Düşünen + Hızlı Üreten İkili**

Nisan 2026'da çıkan `advisor-tool-2026-03-01` beta özelliği çoğu kişinin radarında değil. Bir advisor model (pahalı, zeki) stratejiyi belirler; bir executor model (ucuz, hızlı) token üretir. Kompleks oyun sistemi yazarken:

- **Advisor:** Claude Opus 4.7 — mimariyi tasarlar, edge case'leri yakalar  
- **Executor:** Claude Sonnet 4.6 — kodu üretir, dosyaları düzenler

API'de kullanmak için isteğe `anthropic-beta: advisor-tool-2026-03-01` header'ı ekle. Opus kalitesi + Sonnet fiyatı ve hızı.

---

## Önceki Tahminlerin Doğrulanması

Bu ilk rapordur — önceki tahmin bulunmuyor.

---

## Yakında Gelebilecekler

- **Claude Sonnet 4 + Opus 4 retirement: 15 Haziran 2026** — Bu modelleri kullanan pipeline'ları Sonnet 4.6 / Opus 4.7'ye taşıma zamanı daralıyor.
- **Multiagent Orchestration GA:** Şu an public beta. Tam sürüm geldiğinde indie multi-agent studio setup'ları çok daha stabil olacak.
- **MCP Tunnels yaygınlaşması:** Private server + local tool kombinasyonları ile offline/private geliştirme pipeline'ları kolaylaşacak.
- **Claude Design olgunlaşması:** Visual prototip + GDD + pitch deck aracı Labs'tan çıkıp genel kullanıma girebilir.
- **GameMaker GMRT entegrasyon güncellemesi:** Büyük feature update beklentisi 2026 Q3.
