# Claude Radar Bellek Dosyası
Son güncelleme: 2026-05-25

## Tahmin Doğruluk Takibi
| Tarih | Tahmin | Gerçekleşti mi |
|---|---|---|
| — | İlk rapor, önceki tahmin yok | — |

## Kanıtlanmış Indie Game Dev Kullanımları
- **Godot + Claude Code:** Godot'un text-based dosya yapısı (.gd, .tscn) AI için Unity'den daha uygun
- **GameMaker GMRT + Claude Code** (30 Nisan 2026): Editör içinden doğal dil ile entegrasyon — gerçek, aktif, denenebilir
- **Procedural content generation:** NPC diyalog, dungeon gen, loot table — Claude'un en güçlü game dev use case'i
- **Prompt caching + lore context:** Büyük lore dosyalarını cache'leyerek maliyet %90'a kadar düşürme

## Sürekli Güncel Özellik Listesi
| Yetenek | Mevcut Durum (Mayıs 2026) | Indie Dev Kullanımı |
|---|---|---|
| Kod Yazma | Opus 4.7: %87.6 SWE-Bench (SOTA) | Tam oyun sistemi, refactoring |
| Görsel Yorumlama | Opus 4.7: 3x yüksek çözünürlük | UI mockup analizi, sprite ref |
| Uzun Bağlam | 1M token GA (Sonnet/Opus 4.6+) | Tüm repo context'e sığıyor |
| Paralel Çalışma | Agent View + Multiagent Orch. beta | Aynı anda çok görev |
| Türkçe | Güçlü, doğal | GDD, lore, tasarım dokümanı |
| Agentic Hafıza | Agent Memory public beta | Oturumlar arası öğrenme |

## Geçmiş Büyük Güncellemeler Tarihi
- 2026-04-08: Claude Managed Agents + `ant` CLI launch
- 2026-04-09: Advisor Tool beta (executor + advisor model ikilisi)
- 2026-04-16: Claude Opus 4.7 — SWE-Bench %87.6, 3x görsel çözünürlük
- 2026-04-23: Agent Memory public beta
- 2026-04-30: GameMaker GMRT + Claude Code entegrasyonu
- 2026-05-06: Multiagent Orchestration + Webhooks public beta
- 2026-05-11: Claude Platform on AWS
- 2026-05-12: Fast Mode → Opus 4.7 desteği
- 2026-05-13: Cache Diagnostics public beta
- 2026-05-19: MCP Tunnels (private network) + Self-hosted Sandboxes

## En İyi Prompt Kalıpları (Game Dev için)

### Procedural Generation (Godot odaklı)
```
Sen bir Godot 4 indie oyununda [sistem adı] yazıyorsun.
Çalışma dizini: res://scripts/[klasör]/
Görev: [Dosya adı].gd oluştur.
- [Gereksinim 1]
- [Gereksinim 2]
[Kullanılacak node/sınıf belirt]
Bitince çalıştırma komutunu ver.
```

### NPC Diyalog (cache-friendly)
```
[LORE.md — ilk seferinde tam ver, sonra cache'lenir]
---
NPC: [İsim, yaş, geçmiş, şimdiki durum]
Oyuncu: [Envanter, önceki aksiyonlar]
Üret: [N] diyalog seçeneği + tepki + quest trigger + hafıza notları
```

### Agent View ile Paralel Görev
```
Session 1 (bg): [Uzun süren sistem — pcg, ai, physics]
Session 2 (fg): [Hızlı tamamlanan görev — UI, config, text]
→ Bitince session 1 peek panel'den kontrol et
```

## Dikkat Edilmesi Gerekenler
- **Claude Sonnet 4 + Opus 4 retirement: 15 Haziran 2026** — Geçiş yap
- Claude Haiku 3 kaldırıldı (20 Nisan 2026) — Haiku 4.5'e geç
- Agent View: Research Preview, Claude Code v2.1.139+ gerektirir
- Background sessions lokal — laptop uyursa durur, uzun işlerde dikkat
