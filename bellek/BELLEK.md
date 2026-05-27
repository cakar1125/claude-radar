# Claude Radar Bellek Dosyasi
Son guncelleme: 2026-05-27

## Tahmin Dogruluk Takibi
| Tarih | Tahmin | Gerceklesti mi |
|---|---|---|
| 2026-05-25 | Sonnet 4 + Opus 4 retirement 15 Haziran 2026 | Yaklasıyor |
| 2026-05-25 | Multiagent Orchestration GA | Hala public beta |
| 2026-05-25 | MCP Tunnels yayginlasmasi | Research Preview 19 Mayis da cikti |
| 2026-05-25 | Claude Design (labs cikis) | Henuz belirsiz |
| 2026-05-25 | GameMaker GMRT olgunlasmasi | Q3 2026 devam ediyor |

## Kanitlanmis Indie Game Dev Kullanimlari

- Godot + Claude Code: .gd, .tscn dosyalari AI-dostu; Unity ye gore avantajli
- GameMaker GMRT entegrasyonu (30 Nisan 2026): editor icinden dogal dil ile Claude Code
- Procedural content generation: NPC diyalog, dungeon, loot table -- en guclu use case
- Dreaming ile ogrenen agent (Mayis 2026): kurallari ilk session da ogrenen agent tekrar sormaz
- Outcomes ile kalite kontrolu: tamamlanma kriterini rubric olarak tanimla, agent iterate eder

## Surekli Guncel Ozellik Listesi

| Yetenek | Mevcut Durum | Indie Dev Kullanimi |
|---|---|---|
| Kod Yazma | Opus 4.7: %87.6 SWE-Bench | Oyun sistemi yazimi |
| Gorsel Yorumlama | Opus 4.7: 3x cozunurluk | UI mockup, sprite analizi |
| Uzun Baglam | 1M token GA (Sonnet/Opus 4.6+) | Tum repo context e sigdirma |
| Arac Kullanimi | Agent Skills, MCP, Code Exec GA | Oyun araclarına erisim |
| Paralel Calisma | Multiagent Orchestration (public beta) | Cok gorev ayni anda |
| Agent Bellegi | Dreaming (research preview) | Kuralları oturumlar arasi ogrenme |
| Kalite Kontrolu | Outcomes grader (public beta) | Tamamlanma kriteri + auto-iterate |
| Turkce | Guclu | GDD, lore, tasarim dokumani |

## Gecmis Buyuk Guncellemeler Tarihi

- 2026-04-08: Claude Managed Agents + ant CLI
- 2026-04-09: Advisor Tool beta
- 2026-04-16: Claude Opus 4.7 -- SWE-Bench %87.6
- 2026-04-23: Agent Memory public beta
- 2026-04-30: GameMaker GMRT + Claude Code entegrasyonu
- 2026-05-06: Code with Claude 2026 -- Dreaming, Outcomes, Multiagent, SpaceX compute, 2x limit
- 2026-05-11: Claude Platform on AWS
- 2026-05-12: Fast Mode Opus 4.7
- 2026-05-13: Cache Diagnostics + Claude for Small Business
- 2026-05-18: Stainless satın alması + Web search SEC verileri
- 2026-05-19: MCP Tunnels Research Preview + Self-hosted Sandboxes + KPMG 276K
- 2026-05-22: Project Glasswing -- Claude Mythos 23.019 bug
- 2026-05-22-23: Claude Code v2.1.147-149 -- /code-review, /usage kategorik, diff nav

## En Iyi Prompt Kaliplari (Game Dev icin)

### Procedural Generation
[Oyun turu + engine + dosya yolu]
Gorev: [sistem] olustur. [algoritma]. Bitince test komutu ver.

### NPC Diyalog (cache-friendly)
[LORE.md ilk seferinde tam ver]
NPC: [isim, yas, gecmis]. Oyuncu: [inventory, aksiyonlar].
Uret: [N secenegi] + [tepki+trigger] + [persistent memory notlari]

### Outcomes Rubric
BASARI KRITERLERI: [olculebilir maddeler]
GRADER: pass/fail. Tumu pass -> TAMAMLANDI.

### Dreaming Kurulum
Mimari kurallarim: [klasor, naming, base class, sinyal adi]
Bu oturumda ogren ve [ilk gorev] yap.

## Dikkat

- Sonnet 4 + Opus 4 retirement: 15 HAZIRAN 2026 -- 19 gun kaldi
- Haiku 3 kaldirildi (Nisan 2026) -- Haiku 4.5 e gec
- Dreaming: Research Preview -- Managed Agents API erisimi gerekiyor
- /code-review yeni adi; eski /simplify calismıyor
- /usage v2.1.149+ ile kategorik maliyet dagilimi goruntuluyor
