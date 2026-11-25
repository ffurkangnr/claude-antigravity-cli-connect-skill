# Claude + Antigravity CLI (`agy`) Skill

Bu depo, **Claude Desktop** veya **Claude Code** içerisinden yerel **Google Antigravity CLI (`agy`)** aracını doğrudan çalıştırabilmeniz için hazırlanmış bir **Skill (`SKILL.md`)** paketidir.

Bir kullanıcı bu skill dosyasını Claude'a eklediğinde, Claude arka planda `agy` komutunu nasıl bulacağını, modelleri nasıl listeleyeceğini ve görevleri nasıl devredeceğini otomatik olarak bilir.

## Nasıl Çalışır?

1. Siz Claude'a Antigravity üzerinden bir işlem yapmasını söylersiniz.
2. Claude, `skills/agy-cli/SKILL.md` talimatlarını okuyarak terminal/komut aracı üzerinden `agy -p "..."` komutunu çalıştırır.
3. `agy` CLI, sizin yerel Antigravity hesabınız ve kotanızla (Gemini, Claude vb. modellerle) işlemi gerçekleştirir ve sonucu Claude'a geri döndürür.

> **Not:** Bu entegrasyon Claude'un `agy` komutunu tetiklemesine dayanır; yani Claude'un kendi araç/komut çalıştırma yetkisi ve aktif kotası gerekir.

## Ön Koşullar

- Bilgisayarınızda **Antigravity CLI (`agy`)** kurulu ve giriş yapılmış olmalı.
- **Claude Code** veya komut/dosya aracı aktif bir **Claude Desktop** ortamı.

## Kurulum

### Seçenek 1: Claude Code (Global Skill)
`skills/agy-cli` klasörünü Claude'un global skill dizinine kopyalayın:

- **Windows (PowerShell):**
  ```powershell
  Copy-Item -Recurse .\skills\agy-cli "$env:USERPROFILE\.claude\skills\agy-cli"
  ```
- **macOS / Linux:**
  ```bash
  cp -r ./skills/agy-cli ~/.claude/skills/agy-cli
  ```

### Seçenek 2: Claude Desktop
- `skills/agy-cli/SKILL.md` dosyasını Claude Desktop içindeki ilgili **Project** talimatlarına veya **Custom Skills** bölümüne ekleyin.

## Örnek Kullanım

Skill eklendikten sonra Claude'a şu şekilde komut verebilirsiniz:
- *"Antigravity CLI (`agy`) ile mevcut modelleri listele."*
- *"`agy` kullanarak şu projeyi analiz et ve özet çıkar."*
- *"`agy` üzerinden `--model claude-sonnet-5-5-medium` ile şu soruyu çalıştır."*

## Güvenlik Uyarısı

Bu depoda **hiçbir kişisel token, API anahtarı veya oturum dosyası bulunmaz**. Kendi çatallamanızı (fork) paylaşırken `~/.gemini/` veya `~/.claude/` altındaki kimlik dosyalarını kesinlikle GitHub'a yüklemeyin.
