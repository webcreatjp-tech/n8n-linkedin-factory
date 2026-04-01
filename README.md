# 📱 LinkedIn Content Factory — n8n

Pipeline automatisé de création et publication de contenu LinkedIn. De la veille concurrentielle à la publication, en passant par la génération IA et l'approbation humaine.

## 🔄 Pipeline

```
⏰ Cron 8h → 🕷️ Apify (scraping posts viraux)
           → 🤖 Ollama (génération contenu adapté)
           → 💾 Google Sheets (stockage)
           → 📲 Telegram (notification approbation)
           
✅ Approbation Telegram → 📤 Publication LinkedIn
                        
⏰ Cron 2h → 📊 Stats 48h → 🧠 Analyse patterns → 📲 Rapport Telegram
```

## 📋 Workflows (3)

| Workflow | Déclencheur | Description |
|----------|------------|-------------|
| 01 — Scrape & Generate | Cron 8h00 | Scraping Apify + génération IA + stockage Sheets |
| 02 — Approval Bot | Telegram callback | Approbation/rejet et publication LinkedIn |
| 03 — Feedback 48h | Cron toutes 2h | Collecte stats et analyse des performances |

## 🛠️ Stack

- **Orchestration** : n8n self-hosted
- **Scraping** : Apify (posts LinkedIn viraux)
- **IA** : Ollama local (génération de contenu)
- **Stockage** : Google Sheets (2 onglets : ViralPosts / GeneratedPosts)
- **Approbation** : Telegram Bot
- **Publication** : LinkedIn OAuth2

## ⚙️ Configuration

Variables n8n requises :
- `APIFY_TOKEN` — token Apify pour le scraping
- `LINKEDIN_PERSON_URN` — ton URN LinkedIn (urn:li:person:xxx)
- `TELEGRAM_BOT_TOKEN` — token du bot Telegram
- `TELEGRAM_CHAT_ID` — ton chat ID Telegram

Google Sheets : créer un fichier avec 2 onglets `ViralPosts` et `GeneratedPosts`.
