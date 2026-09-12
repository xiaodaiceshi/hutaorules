# Rules

Automatically generated proxy rule sets for Mihomo, Sing-box, and Surge.

## Update Schedule

- Daily at **02:00 Beijing Time (UTC+8)**

## Directory Structure

```
mihomo/
├── domain/           # 域名规则
│   ├── *.txt         # 文本格式（classical）
│   └── *.mrs         # 二进制格式（编译后）
├── ipcidr/           # IP/CIDR 规则
│   ├── *.txt
│   └── *.mrs
└── *.txt             # 混合规则（classical）

singbox/
├── domain/           # 域名规则
│   └── *.srs         # 二进制格式
├── ip/               # IP/CIDR 规则
│   └── *.srs
└── source/           # 源格式
    └── *.json

surge/
├── *.txt             # RULE-SET 文本格式
└── ipcidr/           # IP/CIDR 规则
    └── *.txt
```

## Format Comparison

| Format | Behavior | Extension | Performance | Memory | Client |
|--------|----------|-----------|-------------|--------|--------|
| MRS | domain / ipcidr | `.mrs` | Excellent | Low | Mihomo |
| Text | classical | `.txt` | Good | Medium | Mihomo |
| SRS | domain / ipcidr | `.srs` | Excellent | Low | Sing-box |
| JSON | source | `.json` | Good | Medium | Sing-box |
| Text | RULE-SET | `.txt` | Good | Medium | Surge |

## Rule Categories

| Category | Description |
|----------|-------------|
| Advertising | Ad domains and IPs |
| Tracking | Privacy & tracking protection |
| Apple | Apple services |
| AppleCN | Apple China-specific domains |
| Telegram | Telegram domains and IPs |
| AI | OpenAI, Claude, Gemini |
| Dev | GitHub, GitLab, Docker, JetBrains |
| SocialMedia | Facebook, Twitter, Instagram, TikTok, Reddit |
| YouTube | YouTube domains and IPs |
| Streaming | Netflix, Disney+, Spotify, HBO, Twitch |
| Speedtest | Speed test services |
| Crypto | Cryptocurrency exchanges |
| Google | Google services and IPs |
| Microsoft | Microsoft services |
| Proxy | Non-China proxy domains |
| China | China mainland domains and IPs |
| Private | Private/LAN networks |
| Emby | Emby media server (manual) |
| EmbyDirect | Emby direct connection (manual) |

## Usage Examples

### Mihomo (Clash.Meta)

```yaml
rule-providers:
  proxy:
    type: http
    behavior: domain
    format: mrs
    url: "https://github.com/huyanluanyuqaq/hutaorules/raw/rules/mihomo/domain/Proxy.mrs"
    interval: 86400

  china:
    type: http
    behavior: domain
    format: mrs
    url: "https://github.com/huyanluanyuqaq/hutaorules/raw/rules/mihomo/domain/China.mrs"
    interval: 86400

  proxy-ip:
    type: http
    behavior: ipcidr
    format: mrs
    url: "https://github.com/huyanluanyuqaq/hutaorules/raw/rules/mihomo/ipcidr/Proxy.mrs"
    interval: 86400
```

### Sing-box

```json
{
  "rules": [
    {
      "rule_set": "geosite-geolocation-!cn",
      "outbound": "proxy"
    },
    {
      "rule_set": "geosite-cn",
      "outbound": "direct"
    }
  ],
  "rule_set": [
    {
      "tag": "geosite-geolocation-!cn",
      "type": "remote",
      "format": "binary",
      "url": "https://github.com/huyanluanyuqaq/hutaorules/raw/rules/singbox/domain/Proxy.srs",
      "download_detour": "direct"
    }
  ]
}
```

### Surge

```ini
[Rule]
RULE-SET,https://github.com/huyanluanyuqaq/hutaorules/raw/rules/surge/Proxy.txt,Proxy
RULE-SET,https://github.com/huyanluanyuqaq/hutaorules/raw/rules/surge/China.txt,DIRECT
```

## Data Sources

| Source | Repository |
|--------|------------|
| MetaCubeX | [meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) |
| blackmatrix7 | [ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) |

## License

[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html)
