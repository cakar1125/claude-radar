# Claude Radar — Ne Yapılabilir?
# GRUP A — Pazartesi, Çarşamba, Cuma, Pazar | 14:30 UTC (17:30 İstanbul)

Bugünün tarihini belirle (YYYY-MM-DD). Claude ve Claude Code'un son yeteneklerini araştır, indie oyun geliştirme için kullanım önerileri sun.

NOT: Repo zaten mevcut dizinde. git komutu KULLANMA. Dosyaları write_file aracıyla yaz.

## ADIM 1 — Önceki raporları oku

list_files ile raporlar/ klasörünü kontrol et. Son 2 raporu read_file ile oku.

## ADIM 2 — Web araması

web_search ile şunları ara:
- "Claude new features [mevcut ay]"
- "Anthropic Claude update today"
- "Claude Code new capabilities"
- "Claude API new endpoints [mevcut ay]"

fetch_url ile `https://docs.anthropic.com/` sayfasını al.

## ADIM 3 — Raporla

write_file ile `raporlar/YYYY-MM-DD_claude-radar.md` oluştur:

```
# [YYYY-MM-DD] Claude Radar

## Bu Dönemde Yenilikler
[Claude / Claude Code'da yeni ne var - liste]

## Indie Oyun Geliştirici İçin En Faydalı 3 Kullanım
1. **[Kullanım adı]**: [Nasıl yapılır, ne işe yarar]
2. **[Kullanım adı]**: ...
3. **[Kullanım adı]**: ...

## Denemeye Değer Prompt/Teknik
[Bu hafta önerilen spesifik bir prompt veya workflow]

## Yakında Gelebilecekler
[Anthropic'in roadmap'inde görünen özellikler]
```
