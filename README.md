# Savasan IHA - Otonom İHA Entegrasyonu

Toy-Siha tarafından geliştirilen, otonom hava araçları (İHA) üzerine çalışan kapsamlı bir proje koleksiyonudur. Farklı kontrol sistemleri, simülasyon ortamları ve araçları içeren modüler bir yapıya sahiptir.

---

## 📁 Proje Yapısı

### 🛩️ **DogFight**
Drone combat simülasyonu ve kontrolü için geliştirilmiş ana modül.

- **gps_bearing_calculator.py** - GPS koordinatlarından açı ve mesafe hesaplama
- **gazebo_simulation/** - Gazebo simülasyon ortamı
  - **models/** - Drone ve sistem modelleri
    - `gimbal_small_*` (1D, 2D, 3D) - Kamera gimbal modelleri
    - `iris_with_ardupilot` - Iris dronu Ardupilot desteğiyle
    - `iris_with_gimbal` - Gimbal eklenmiş Iris dronu
    - `iris_with_standoffs` - Standoff'larla modifiye edilmiş Iris
    - `parachute_small` - Küçük paraşüt modeli
    - `rc_cessna` - RC Cessna uçak modeli
    - `runway` - Pist modeli
    - `zephyr_*` - Zephyr UAV modelleri (normal, Ardupilot, paraşütlü)
  - **scripts/** - Kurulum ve başlatma scripteleri
    - `install.sh` - Bağımlılık kurulumu
    - `start_simulation.sh` - Simülasyonu başlatma
  - **worlds/** - Simülasyon ortam dosyaları (.sdf)
    - Baylands, gimbal, pist, depo sahneleri
- **px4_msgs/** - PX4 mesaj tanımları
- **px4_ros_com/** - PX4 ve ROS2 haberleşmesi
- **ros2_ws/src/object_detection/** - Nesne algılama modülü

### 🎯 **mock_server**
WebSocket tabanlı mock server ve test amaçlı senaryolar.

- **server/ws_server.py** - WebSocket server
- **clients/ws_test_client.py** - Test client
- **config/hss_zones.json** - Hava Trafik Yönetimi (HSS) bölgeleri yapılandırması
- **dashboard/** - Web tabanlı dashboard
  - `app.js` - Frontend uygulaması
  - `index.html` - UI şablonu
  - `icons/` - İkon kaynakları
- **scenarios/** - Önceden tanımlanmış test senaryoları
  - `base_generator.py` - Senaryo tabanı
  - `approach.py` - Yaklaşım senaryosu
  - `avoidance.py` - Çarpışmadan kaçınma
  - `circular.py` - Dairesel yol izleme
  - `hss_approach.py` - HSS yaklaşımı
  - `straight.py` - Doğru yol izleme

### 🏆 **TEKNOFEST2026_fighter_uav_integration**
TEKNOFEST 2026 savaştırıcı İHA entegrasyon projesi.

- **mock/** - Mock server bileşenleri (mock_server ile benzer)
- **px4_msgs/** - PX4 mesaj tanımları
- **teknofest_control/** - Ana kontrol paketi (ROS2)
  - **config/** - Parametreler (tracking, mock tracking)
  - **scripts/** - Kontrol scriptleri
  - **launch/** - ROS2 launch dosyaları
- **teknofest_simulation/** - Simülasyon ortamı
  - **models/** - Drone modelleri
  - **worlds/** - Simülasyon sahneleri
- **teknofest_vision/** - Görüntü işleme ve algılama
  - **launch/** - Vision launch dosyaları

### 📍 **toy-tctrackpp**
Takip sistemi (Tracking) için geliştirilen kütüphane.

- **src/takip_sistemi/** - Takip sistemi kaynak kodları

### 🖥️ **yki_backend**
Arka uç API servisi.

- **main.py** - Uygulama giriş noktası
- **config.py** - Yapılandırma ayarları
- **backend/** - Ana servis modülleri
  - `api_client.py` - API client
  - `camera_stream.py` - Kamera akışı işleme
  - `hss.py` & `hss_fetcher.py` - HSS entegrasyonu
  - `telemetry_manager.py` - Telemetri yönetimi
  - `uav.py` - UAV kontrol sınıfı
  - `map_manager.py` - Harita yönetimi
  - `requirements.txt` - Python bağımlılıkları

### 📊 **yki_dashboard_ui**
PyQt5 tabanlı masaüstü dashboard uygulaması.

- **main.py** - Uygulama başlatıcı
- **config.json** - Yapılandırma dosyası
- **core/** - Temel modüller
  - `drone_state.py` - Drone durumu takibi
  - `serial_reader.py` - Serial haberleşme
  - `sitl_reader.py` - SITL simülatör okuyucu
  - `server_sender.py` - Server iletişimi
- **ui/** - Arayüz bileşenleri
  - `dashboard.py` - Ana dashboard
  - `map_widget.py` - Harita gösterimi
  - `video_widget.py` - Video akışı
- **utils/** - Yardımcı fonksiyonlar
  - `config.py` - Yapılandırma yönetimi
  - `helpers.py` - Yardımcı fonksiyonlar
- **video/** - Video işleme
  - `video_thread.py` - Video akışı thread'i
  - `qr_camera_thread.py` - QR kod okuma

---

## 🚀 Hızlı Başlangıç

### Gereksinimler
- ROS2 (DogFight ve TEKNOFEST2026 için)
- Python 3.8+
- Gazebo Sim
- PX4 Autopilot

### DogFight Simülasyonu Başlatma
```bash
cd DogFight/gazebo_simulation
./scripts/install.sh
./scripts/start_simulation.sh
```

### Mock Server Başlatma
```bash
cd mock_server
python server/ws_server.py
```

### YKI Dashboard Başlatma
```bash
cd yki_dashboard_ui
pip install -r requirements.txt
python main.py
```

### YKI Backend Başlatma
```bash
cd yki_backend
pip install -r backend/requirements.txt
python backend/main.py
```

---

## 📝 Proje Açıklamaları

| Proje | Amaç | Teknoloji |
|-------|------|-----------|
| **DogFight** | Drone combat simülasyonu ve kontrolü | Gazebo, PX4, ROS2 |
| **mock_server** | Test senaryoları ve websocket server | Python, WebSocket |
| **TEKNOFEST2026** | TEKNOFEST savaş drone entegrasyonu | ROS2, PX4, Python |
| **toy-tctrackpp** | UAV takip sistemi | Python |
| **yki_backend** | Merkezi arka uç servisi | Python, FastAPI |
| **yki_dashboard_ui** | Masaüstü kontrol paneli | PyQt5, Python |

---

## 🔗 Bağlantılar

- **DogFight**: https://github.com/yunusemretom/DogFight
- **yki_backend**: https://github.com/emine370/yki_backend
- **yki_dashboard_ui**: https://github.com/emine370/yki_dashboard_ui
- **mock_server**: https://github.com/emine370/mock_server
- **TEKNOFEST2026**: https://github.com/meryem-zeynep-ozdogan/TEKNOFEST2026_fighter_uav_integration
- **toy-tctrackpp**: https://github.com/tugbatrl/toy-tctrackpp

---

## 📌 Notlar

- Proje, Git submodul'ler olarak yapılandırılmıştır
- Her modül bağımsız olarak kullanılabilir
- ROS2 temelli iletişim standart olarak kullanılmaktadır
- Simülasyon ve gerçek ortam desteği mevcuttur

