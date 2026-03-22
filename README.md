# Qanot Plugins Registry

Official plugin registry for [Qanot AI](https://github.com/QANOT/qanot) — the AI agent framework for Telegram bots.

## Install a Plugin

```bash
# From registry
qanot plugin install bito

# From git URL
qanot plugin install https://github.com/QANOT/qanot-plugin-bito.git

# User-level (shared across projects)
qanot plugin install bito --user
```

## Available Plugins

| Plugin | Description | Tags |
|--------|-------------|------|
| **amocrm** | amoCRM CRM integration — leads, contacts, pipelines, tasks | crm, sales |
| **bitrix24** | Bitrix24 CRM integration — deals, leads, contacts, tasks | crm, sales |
| **bito** | Bito POS/ERP — sotuvlar, tovarlar, mijozlar, ombor | pos, erp |
| **moysklad** | MoySklad — tovarlar, ombor, sotuvlar, xaridlar | erp, inventory |
| **onec** | 1C Enterprise — contractors, products, sales, balances | erp, 1c |
| **ibox** | ibox.io ombor boshqaruv tizimi | inventory, pos |
| **eskiz** | Eskiz SMS gateway — xabar yuborish, balans | sms, notification |
| **mysql_query** | MySQL SELECT-only query (500-row limit, 5s timeout) | database, sql |
| **absmarket** | AbsMarket POS — 30 API tools + MySQL | pos, market |
| **absvision** | AbsVision HR — 25 HR tools with OAuth | hr, employees |
| **cloud_reporter** | Reports usage metrics to Qanot Cloud | internal, metrics |

## Search

```bash
qanot plugin search crm
qanot plugin search pos
qanot plugin search sms
```

## Security

Every plugin is scanned on install for:
- Dangerous files (`install.sh`, `.exe`, `.bat`, `.env`)
- Malicious code patterns (`os.system`, `eval`, `exec`, `subprocess`, `keylogger`, `stealer`)
- Untrusted dependencies (allowlist-only pip install)
- SHA256 integrity hashes stored in `plugins.lock.json`

```bash
# Scan a plugin manually
qanot plugin scan bito

# Verify all plugin hashes
qanot plugin verify
```

## Create Your Own Plugin

```bash
# Scaffold
qanot plugin new my_plugin

# Structure
plugins/my_plugin/
  plugin.json    # manifest (name, version, deps)
  plugin.py      # QanotPlugin class with @tool decorators
```

See [Plugin Development Guide](https://github.com/QANOT/qanot/blob/main/docs/plugins.md) for details.

## Submit a Plugin

1. Create a repo: `qanot-plugin-<name>`
2. Include `plugin.py` + `plugin.json`
3. Open a PR to add your entry to `index.json`

All submissions are reviewed for security before inclusion.
