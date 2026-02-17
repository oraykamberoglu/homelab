# 🚀 Multi-Node Linux Homelab Infrastructure

![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-active-success)
![Platform](https://img.shields.io/badge/platform-linux-blue)
![Maintained](https://img.shields.io/badge/maintained-yes-brightgreen)

> Production benzeri çok makineli Linux altyapı ortamı — Reverse Proxy, Network Segmentation ve Service Architecture içeren gerçekçi lab projesi.

---

## 📌 Proje Amacı

Bu projenin amacı tek bir bilgisayar üzerinde sanallaştırma kullanarak gerçek dünyadaki sunucu mimarilerini simüle etmek ve aşağıdaki DevOps / System Engineering konseptlerini pratik etmektir:

* Reverse Proxy mimarisi
* Multi-node network topolojisi
* Internal subnet yönetimi
* Service isolation
* Firewall kontrolü
* Port routing
* Infrastructure provisioning

---

## 🏗 Mimari Diyagram

> docs/architecture.png dosyasını eklediğinde GitHub otomatik gösterecek

```
Client  →  Gateway (Nginx Reverse Proxy)  →  App Server (Apache)
```

---

## 🖥 Sunucu Rolleri

| Sunucu  | Rol           | Açıklama                  |
| ------- | ------------- | ------------------------- |
| client  | Test makinesi | HTTP istekleri gönderir   |
| gateway | Reverse Proxy | Trafiği yönlendirir       |
| app     | Web Server    | Apache ile uygulama sunar |

---

## 🌐 Network Planı

| Interface | IP            | Açıklama |
| --------- | ------------- | -------- |
| gateway   | 192.168.56.10 | Proxy    |
| app       | 192.168.56.11 | Backend  |
| client    | 192.168.56.12 | User     |

---

## ⚙️ Kullanılan Teknolojiler

* Linux
* Nginx
* Apache
* Vagrant
* VirtualBox
* systemd
* firewalld
* iproute2 tools

---

## 📦 Kurulum

### 1 — Repo Klonla

```bash
git clone https://github.com/USERNAME/homelab.git
cd homelab
```

### 2 — Ortamı Başlat

```bash
vagrant up
```

### 3 — Makinelere Bağlan

```bash
vagrant ssh gateway
vagrant ssh app
vagrant ssh client
```

---

## 🔁 Trafik Testi

Client makinede:

```bash
curl http://192.168.56.10
```

Beklenen çıktı:

```
Apache Test Page
```

---

## 🔐 Firewall Ayarları

```bash
sudo firewall-cmd --add-service=http --permanent
sudo firewall-cmd --reload
```

---

## 🤖 Otomatik Deploy (Opsiyonel CI/CD)

Projeyi otomatik ayağa kaldırmak için örnek GitHub Actions workflow:

`.github/workflows/lab.yml`

```yaml
name: Homelab Test

on: [push]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - name: Validate Vagrantfile
        run: vagrant validate
```

---

## 📊 Öğrenilen Konseptler

* Reverse proxy mimarisi
* Network segmentation
* Internal routing
* Service orchestration
* Port conflict çözme
* Process monitoring
* Infrastructure thinking

---

## 📈 Roadmap

* [ ] Load Balancer cluster
* [ ] HTTPS termination
* [ ] Monitoring stack
* [ ] Central logging server
* [ ] Failover sistemi
* [ ] Docker versiyonu
* [ ] Kubernetes deploy

---

## 🧪 Test Senaryoları

| Test           | Beklenen Sonuç    |
| -------------- | ----------------- |
| Gateway kapat  | erişim kesilir    |
| App restart    | servis geri gelir |
| Firewall block | trafik reddedilir |

---

## 📁 Proje Yapısı

```
homelab/
 ├── Vagrantfile
 ├── README.md
 ├── configs/
 │    ├── nginx.conf
 │    └── apache.conf
 ├── docs/
 │    └── architecture.png
 └── scripts/
      └── provision.sh
```

---

## 🧠 Bu Proje Ne Öğretir?

Bu lab ortamı küçük ölçekli olsa da aşağıdaki gerçek production mimarilerinin mantığını öğretir:

* Cloud altyapı mantığı
* Load balancer davranışı
* Network isolation
* Backend servis mimarisi
* Proxy katmanı yönetimi

---

## 👨‍💻 Author

**Oray**
DevOps Engineer Journey 🚀

---

## 🤝 Katkı Sağla

Pull request açabilir veya issue oluşturabilirsin.

---

## 📜 Lisans

MIT License
