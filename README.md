# macchanger
# MyMacChanger

## Açıklama
MyMacChanger, kullanıcıların Linux sistemlerinde **MAC adreslerini değiştirmelerine** yardımcı olan bir Python aracıdır. Bu araç, komut satırından verilen arayüz ve yeni MAC adresi bilgilerine göre ilgili ağ arayüzünün MAC adresini değiştirir.

## Gereksinimler
- Python 3.x
- Linux işletim sistemi
- root yetkileri (sudo)

## Kurulum
Öncelikle, gerekli Python paketlerinin sisteminizde kurulu olduğundan emin olun:
```bash
sudo apt update
sudo apt install python3
```

Ardından, **MyMacChanger.py** dosyasını indirip çalıştırılabilir hale getirin:
```bash
chmod +x mymacchanger.py
```

## Kullanım
Komut satırında aşağıdaki gibi çalıştırabilirsiniz:
```bash
sudo python3 mymacchanger.py -i <interface> -m <new_mac>
```
Örnek:
```bash
sudo python3 mymacchanger.py -i eth0 -m 00:11:22:33:44:55
```

### **Parametreler**
| Parametre | Açıklama |
|-----------|---------|
| `-i` veya `--interface` | MAC adresi değiştirilecek ağ arayüzü (örneğin: `eth0`, `wlan0`) |
| `-m` veya `--mac` | Yeni MAC adresi (örneğin: `00:11:22:33:44:55`) |

## Çalışma Mantığı
1. **Kullanıcıdan giriş alır**: Hangi arayüzün MAC adresinin değiştirileceğini ve yeni MAC adresini belirler.
2. **Arayüzü devre dışı bırakır**: `ifconfig <interface> down` komutuyla belirtilen ağ arayüzünü kapatır.
3. **MAC adresini değiştirir**: `ifconfig <interface> hw ether <new_mac>` komutuyla yeni MAC adresini atar.
4. **Arayüzü yeniden etkinleştirir**: `ifconfig <interface> up` komutuyla ağ arayüzünü açar.
5. **MAC adresinin değiştiğini kontrol eder**: Yeni MAC adresinin başarılı bir şekilde atanıp atanmadığını doğrular.

## Olası Hatalar ve Çözümleri
- **Hata:** `Error!` mesajı alıyorsanız MAC adresi değiştirilememiş olabilir. Çözüm için şunları deneyin:
  - Root yetkisi ile çalıştırdığınızdan emin olun: `sudo`
  - Girdiğiniz MAC adresinin doğru formatta olduğundan emin olun.
  - Ağ arayüzünün adını yanlış yazmadığınıza dikkat edin (`ifconfig` ile kontrol edebilirsiniz).

## Notlar
- Bu araç sadece **Linux** sistemlerinde çalışır.
- `ifconfig` komutu bazı sistemlerde varsayılan olarak gelmeyebilir. Eğer çalışmıyorsa, şu komutla yükleyebilirsiniz:
```bash
sudo apt install net-tools
```

## Yasal Uyarı
Bu aracı **yalnızca eğitim amaçlı ve yasal çerçevede** kullanın. İzinsiz ağ değişiklikleri yapmak **yasal sonuçlar doğurabilir**. Kullanıcı, bu aracı kullanırken oluşabilecek her türlü durumdan **kendisi sorumludur**.

---
**Geliştirici:** [Senin Adın]  
**İletişim:** [Senin Mailin veya Github Adresin]


