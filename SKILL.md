---
name: wazuh-connector
description: Skill untuk integrasi dengan Wazuh SIEM guna manajemen agen dan monitoring keamanan.
metadata:
  openclaw:
    requires:
      env: 
        - WAZUH_API_USER
        - WAZUH_API_PASSWORD
        - WAZUH_API_URL
      bins: 
        - curl
        - jq
---

# Wazuh API Connector

Skill ini memungkinkan agen untuk berinteraksi dengan API Manager Wazuh untuk melakukan investigasi keamanan dan manajemen aset.

## Instruksi Operasional

1. **Autentikasi**:
   Selalu awali dengan mendapatkan token JWT menggunakan kredensial dari environment variables:
   ```bash
   TOKEN=$(curl -u "$WAZUH_API_USER:$WAZUH_API_PASSWORD" -k -X POST "$WAZUH_API_URL/security/user/authenticate?raw=true")
