Harika, global kurulumu tamamlamışsın! Şimdi elinde `tsc` (TypeScript Compiler) komutu var. 

Aklında net olsun: **Node.js doğrudan `.ts` uzantılı dosyayı çalıştıramaz.** Onu önce JavaScript'e çevirmen (derleme/transpile) gerekir. İşte adım adım yapman gerekenler:

---

### 🚀 1. Standart Yöntem: Derleyip Çalıştırma
En temel ve resmi yoldur.

**Adım 1:** `deneme.ts` adında bir dosya oluştur ve içine basit bir kod yaz.
```typescript
// deneme.ts
const mesaj: string = "Merhaba TypeScript!";
console.log(mesaj);
```

**Adım 2:** Terminalde dosyanın bulunduğu klasöre gel ve derleme komutunu çalıştır:
```bash
tsc deneme.ts
```
> Bu komut, aynı klasör içinde **`deneme.js`** adında yepyeni bir JavaScript dosyası oluşturacaktır.

**Adım 3:** Oluşan JavaScript dosyasını Node.js ile çalıştır:
```bash
node deneme.js
```
Ekranda `Merhaba TypeScript!` yazısını görmelisin.

---

### ⚡ 2. Otomatik İzleme (Watch) Modu
Her değişiklikte manuel olarak `tsc dosya.ts` yazmak sıkıcıdır. TypeScript'i izleme moduna alabilirsin:

```bash
tsc --watch deneme.ts
```
Terminal kapanmaz, dosyayı kaydettiğin an otomatik olarak `.js` dosyası güncellenir. Sonra başka bir terminal açıp `node deneme.js` ile çalıştırmaya devam edersin.

---

### 🏗️ 3. Profesyonel Yöntem: `tsconfig.json` Kullanımı
Eğer birden fazla `.ts` dosyan varsa, her seferinde dosya ismi yazmak yerine bir proje yapılandırma dosyası oluşturmalısın.

**Adım 1:** Proje klasöründe aşağıdaki komutu çalıştır (Bu dosya tüm ayarları tutar):
```bash
tsc --init
```
Klasöründe `tsconfig.json` oluşacaktır.

**Adım 2:** Derlemek için sadece şunu yaz:
```bash
tsc
```
Bu komut, klasördeki **tüm** `.ts` dosyalarını yakalar ve `.js`'e çevirir. 
**Adım 3:** Çıktıyı yine `node` ile çalıştırırsın.

---

### 🔥 4. Tek Komutta Çalıştırma (Önerilen Kolaylık: `ts-node`)
Yukarıdaki yöntemler (derle + çalıştır) iki ayrı adım gerektirir. Eğer sürekli test ediyorsan, **`ts-node`** adlı aracı kullanabilirsin. Bu araç arka planda derler ve hemen çalıştırır.

**Kurulum (global olarak):**
```bash
npm install -g ts-node
```
**Kullanımı (artık tek komut yeterli!):**
```bash
ts-node deneme.ts
```
> *Not: Bu yöntem, özellikle öğrenme aşamasında çok pratiktir çünkü ortaya `.js` dosyası çıkarmaz, direkt sonucu görürsün.*

---

### ⚠️ Karşılaşabileceğin Olası Hatalar ve Çözümleri

| Hata | Çözüm |
| :--- | :--- |
| `'tsc' recognized as an internal or external command` | Terminali **yeniden başlat** (Yeni bir CMD/PowerShell aç). Global kurulumdan sonra PATH güncellenmez bazen. |
| `Cannot find module 'typescript'` | Eğer `ts-node` kullanıyorsan ve bu hatayı alıyorsan, proje klasöründe `npm install typescript` ile lokal olarak da kurmayı dene. |
| Derleme oldu ama çalışmıyor | `console.log` falan yazdıysan sorun yoktur. TypeScript, ES5/ES6 JS koduna dönüştürür, Node rahatça çalıştırır. |

---

### 📝 Sana Özel Pratik Akışı
Öğrenme aşamasında en rahat edeceğin yöntem şu olsun:

1. Klasör oluştur, içinde `tsc --init` yap (config dosyan olsun).
2. VS Code aç ve `deneme.ts` yaz.
3. Terminali böl (split). Bir tarafta `tsc --watch` çalıştır (otomatik derleme için).
4. Diğer tarafta `node deneme.js` ile sonuçları izle.

Ya da en kolayı, `ts-node deneme.ts` diyerek direkt çalıştır. 

Hangisini denedin? Takıldığın bir nokta olursa terminal çıktısını bana atabilirsin, yardımcı olayım! 🚀
