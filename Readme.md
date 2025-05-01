# Orion & Atom CMS – Geliştirme ve Hata Düzeltme Reposu  
## Orion & Atom CMS – Development and Bugfix Repository

Bu depo, **Orion CMS** ve **Atom CMS** projelerindeki hataların giderilmesi ve yeni özelliklerin eklenmesi amacıyla oluşturulmuştur. Açık kaynak felsefesiyle herkesin katkısına açıktır.

This repository is created to fix bugs and implement new features for **Orion CMS** and **Atom CMS**. Contributions are welcome from anyone in the spirit of open source.

---

## 🚀 Katkıda Bulunmak / Contributing

- Hataları bildirin veya çözün  
- Yeni özellikler önerin ya da geliştirin  
- Kodunuzu forkladıktan sonra pull request gönderin

Report or fix bugs, suggest or develop new features, and send a pull request after forking the repository.

---

## 🛠️ Sık Karşılaşılan Sorun ve Çözümü / Common Issue & Fix

### ❗ Problem  
**"Your IP address seems to be invalid"** hatası alıyorsanız, bu genellikle Cloudflare veya benzeri proxy servislerinin kullanıldığı durumlarda gerçek IP adresinin alınamamasından kaynaklanır.

### ✅ Çözüm / Solution

Dosya yolu:  
`/app/Actions/Fortify/CreateNewUser.php`

Şu satırı bulun:

```php
$userIp = request()->ip();
```

Bununla değiştirin:

```php
$userIp = request()->header('CF-Connecting-IP') ?? request()->ip();
```

Bu düzenleme, Cloudflare üzerinden gelen doğru IP adresini almanızı sağlar.

---
