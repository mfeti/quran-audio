# 🎙️ Quran Audio Collection - Multi-Reciter CDN

[![jsDelivr](https://data.jsdelivr.com/v1/package/gh/mfeti/quran-audio/badge)](https://www.jsdelivr.com/package/gh/mfeti/quran-audio)
[![GitHub release](https://img.shields.io/github/v/release/mfeti/quran-audio)](https://github.com/mfeti/quran-audio/releases)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Ethiopia 🇪🇹](https://img.shields.io/badge/🌍-Ethiopia_Ready-12a8ff)](https://github.com/mfeti/quran-audio)

## 📖 About

Free, high-quality Quran audio files for developers and Islamic apps. Served via **jsDelivr CDN** - fast, reliable, and 100% free!

### ✨ Features

- 🎵 **Multiple reciters** - Choose your favorite qari
- 📦 **CDN powered** - Blazing fast delivery worldwide
- 🔄 **Versioned releases** - Never break your production apps
- 💰 **Completely free** - No API keys, no limits
- 🇪🇹 **Amharic ready** - Perfect for Ethiopian Quran apps

## 🎧 Available Reciters

| Reciter            | Style    | Quality | Size  | Complete      |
| ------------------ | -------- | ------- | ----- | ------------- |
| **Mishari Rashid** | Murattal | 192kbps | 2.4GB | ✅ 114 Surahs |
| **Abdul Basit**    | Murattal | 128kbps | 1.8GB | ✅ 114 Surahs |
| **Saad Al-Ghamdi** | Murattal | 192kbps | 2.1GB | ⚠️ 112/114    |
| **Al-Afasy (Low)** | Murattal | 48kbps  | 650MB | ✅ 114 Surahs |
| **Sudais**         | Murattal | 128kbps | 1.9GB | ✅ 114 Surahs |

> 🔥 **For Ethiopian users**: Use `al-afasy` (48kbps) for best performance on mobile networks

## 🚀 Quick Start

### Base URL Pattern

https://cdn.jsdelivr.net/gh/mfeti/quran-audio@v1.0.0/{RECITER}/{SURAH}/{AYAH}.mp3

### Examples

```javascript
// Mishari Rashid - Surah Al-Fatiha (1:1)
const url =
  "https://cdn.jsdelivr.net/gh/mfeti/quran-audio@v1.0.0/mishari-rashid/001/001.mp3";

// Abdul Basit - Ayatul Kursi (2:255)
const url =
  "https://cdn.jsdelivr.net/gh/mfeti/quran-audio@v1.0.0/abdul-basit/002/255.mp3";

// Low quality for mobile (Al-Afasy)
const url =
  "https://cdn.jsdelivr.net/gh/mfeti/quran-audio@v1.0.0/al-afasy/114/006.mp3";
```

## 💻 Usage in Your App

### JavaScript/TypeScript

```javascript
function getQuranAudioUrl(reciter: string, surah: number, ayah: number): string {
  const surahPadded = surah.toString().padStart(3, '0');
  const ayahPadded = ayah.toString().padStart(3, '0');

  return `https://cdn.jsdelivr.net/gh/mfeti/quran-audio@v1.0.0/${reciter}/${surahPadded}/${ayahPadded}.mp3`;
}

// Usage
const audioUrl = getQuranAudioUrl('mishari-rashid', 1, 1);
```

### React Component

```javascript
function QuranPlayer({ surah, ayah, reciter = "mishari-rashid" }) {
  const [audioUrl, setAudioUrl] = useState("");

  useEffect(() => {
    const surahPadded = String(surah).padStart(3, "0");
    const ayahPadded = String(ayah).padStart(3, "0");
    const url = `https://cdn.jsdelivr.net/gh/mfeti/quran-audio@v1.0.0/${reciter}/${surahPadded}/${ayahPadded}.mp3`;
    setAudioUrl(url);
  }, [surah, ayah, reciter]);

  return <audio controls src={audioUrl} />;
}
```

### HTML

```html
<audio controls>
  <source
    src="https://cdn.jsdelivr.net/gh/mfeti/quran-audio@v1.0.0/mishari-rashid/001/001.mp3"
    type="audio/mpeg"
  />
  Your browser does not support the audio element.
</audio>
```

### 📂 Folder Structure

---

## 🎯 Reciter IDs for API Calls

```javascript
const RECITERS = {
  MISHARI_RASHID: "mishari-rashid", // High quality, popular
  ABDUL_BASIT: "abdul-basit", // Classic recitation
  SAAD_AL_GHAMDI: "saad-al-ghamdi", // Beautiful voice
  AL_AFASY_LOW: "al-afasy", // 📱 Mobile optimized (48kbps)
  SUDAIS: "sudais", // Haram Imam
};
```

## 🌐 CDN Networks

This repository is automatically distributed via:

- **jsDelivr** - Primary CDN (global)
- **Fastly** - Edge caching
- **Cloudflare** - Additional backup

## 📦 Versioning

We use semantic versioning with Git tags:

| Version   | Status        | CDN URL          |
| --------- | ------------- | ---------------- |
| `@latest` | Development   | `.../main/...`   |
| `@v1.0.0` | Stable ✅     | `.../v1.0.0/...` |
| `@v1`     | v1.x.x latest | `.../v1/...`     |

> ⚠️ **Always use version tags in production!** Never use `@latest` in production apps.

## 🔧 Installation for Developers

### Download via Git

```bash
# Clone specific reciter only (saves bandwidth)
git clone --depth 1 --filter=blob:none --sparse https://github.com/mfeti/quran-audio.git
cd quran-audio
git sparse-checkout set mishari-rashid

# Clone everything
git clone https://github.com/mfeti/quran-audio.git


```

### Download via wget

```bash
# Download single ayah
wget https://cdn.jsdelivr.net/gh/mfeti/quran-audio@v1.0.0/mishari-rashid/001/001.mp3

# Download entire surah
for i in {001..007}; do
  wget https://cdn.jsdelivr.net/gh/mfeti/quran-audio@v1.0.0/mishari-rashid/001/$i.mp3
done
```

## 📊 Statistics

| Reciter        | Total Files | Total Size | Complete |
| -------------- | ----------- | ---------- | -------- |
| mishari-rashid | 6,236       | 2.4GB      | ✅       |
| abdul-basit    | 6,236       | 1.8GB      | ✅       |
| saad-al-ghamdi | 6,116       | 2.1GB      | ⚠️       |
| al-afasy       | 6,236       | 650MB      | ✅       |
| sudais         | 6,236       | 1.9GB      | ✅       |
| **Total**      | **31,060**  | **8.85GB** | -        |

## 🤝 Contributing

### Add a New Reciter

1. Fork this repository
2. Create folder: `new-reciter-name/`
3. Add surah folders: `001/`, `002/`, etc.
4. Add MP3 files (3-digit naming: `001.mp3`)
5. Update `reciters.json`
6. Submit a Pull Request

### File Naming Rules

- Surah folders: `001` to `114` (3 digits)
- Ayah files: `001.mp3` to `999.mp3` (3 digits)
- Reciter folders: lowercase with hyphens (`mishari-rashid`)
- No spaces or special characters

## 📜 License

This repository contains **public domain Quranic recitations**. All audio files are freely available for any use.

- **Recitations**: Free for all uses
- **Code**: MIT License

## ❤️ Support

- 🇪🇹 **Ethiopian users**: Use `al-afasy` reciter for best performance
- 🐛 **Issues**: Open a GitHub issue
- 💬 **Questions**: Discussions tab
- 🌟 **Star this repo** if you find it useful!

## 🕌 Recommended Reciters for Ethiopian Users

| Network Speed | Recommended Reciter | Quality |
| ------------- | ------------------- | ------- |
| 2G/3G (Slow)  | Al-Afasy            | 48kbps  |
| 4G (Medium)   | Abdul Basit         | 128kbps |
| WiFi/Fast     | Mishari Rashid      | 192kbps |

## 🔗 Related Projects

- [Quran API](https://github.com/semarketir/quran-api) - Complete Quran API
- [Amharic Quran App](https://github.com/yourusername/amharic-quran) - Quran app for Ethiopians
- [Quran Audio Player](https://github.com/yourusername/quran-player) - Custom audio player

## 📞 Contact

- GitHub: [@mfeti](https://github.com/mfeti)
- Project Link: [https://github.com/mfeti/quran-audio](https://github.com/mfeti/quran-audio)

---

**⭐ Don't forget to star this repository if it helped you!**

Made with ❤️ for the Ummah | 🇪🇹 Special focus on Ethiopian Muslims
