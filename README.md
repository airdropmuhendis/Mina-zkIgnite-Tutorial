<h1 align="center">Mina Protocol Berkley Testnet (ZKapp oluşturma)

## Mina Protocol, Layer-1 blok zincirleri arasında “minimal” blok zinciri olarak tanımlanan ve bilinen en hafif blok zinciri olma ünvanına sahiptir. Ölçeklendirme adına gelecekte çok fazla konuşulacak bir proje (boyut sadece 22kb). Bu rehberde sizlerle beraber mina berkley ağı üzerinde zkspark oluşturarak 250.000 MİNA ödüllü yarışmasına katılacağız. Temel eğitimler [Mina Docs](https://docs.minaprotocol.com/zkapps/tutorials/hello-world) üzerinde bulunuyor. burda bireysel geliştirmeler yapmanız gerekecek ancak temel yapmanız gereknleri sizlere aktarmaya çalışacağız.

## Video [Linki](https://youtu.be/62I0tvTnEfQ) 

## Sunucuyu nerden nasıl alacağınızı bilmiyorsanız node eğitim serimizi izleyebilirsiniz. [Node Eğitim Serisi](https://www.youtube.com/playlist?list=PLKxGUfdcj7MVXls2OvTpwx6CnpVJN685w) veya bir önce kurduğumuz manta suncunuzu sıfırlayarak kurabilirsiniz işlemler tamamlandıktan sonra sunucuyu isterseniz tamamen silebilirsiniz. 
 
![image](https://docs.minaprotocol.com/img/homepage/zkapp_developers.png)
## Tekrar hatırlatalım ödüllü bir testnet değil sadece projeyi ilerlyen zamnlarda çok sık duyacağımızı düşünüyoruz bu yüzden öğrenmek hepimiz için iyi olacaktır ve yazılım konusunda kendini geliştirmek isteyen arkadaşlarımız için bir önayak konumunda olsun.
  
## Ödül ve şartlar hakkında [Link](https://minaprotocol.com/blog/zkspark-cohort0)
 
 ## Cüzdan kurlumu ve test tokenleri

- Auro Cüzdanı indir https://www.aurowallet.com/
- Berkley ağında cüzdan adresimizi yazarak test tokenlerini alıyoruz https://faucet.minaprotocol.com/ yeni blok eklenince test tokenleri gelecektir. Bloklaraı [burdan] (https://berkeley.minaexplorer.com) kontrol edebilirsiniz.

  
### Sistem Gereksinimleri
 - kurulum için sistemin özellikleri çok önemli değil, zaten bitirdikten sonra vps sıfırlayacağız dileyen arkadaşlar silebilir. kurulumu için node js üzerinde ilerleteceğiz, ben ubunutu üzerinde node js kurarak devam edeceğim dilerseniz aldığınız sunucuyu direk nodejs uyumlu alabilirsiniz.
 - NodeJS 16+
 - NPM 6+
 - Git 2+
 - disk boyutu önemsiz

<h1 align="center">Örnek Kurulum
  

  ## Root yetkisi almak için aşağğıdaki kodu giriyoruz bazı sunucularda bunu sürekli girmemiz gerekiyor. eğer bunu girmezseniz yazdığınız kodun başına sudo komutunu yazarkata devam edebilirsiniz ancak karışıklık olmaması için aşğıdaki komutu yazmanızı tavsiye ederim. ( root: Windows cihazlarda olduğu gibi yönetici olarak çalıştırmamıza, yani bize yetki veren bir komuttur.)
  ```
  sudo su
  cd
  ```

 ## Aşşağıdaki komutlarla sunucumuzdaki güncellemeleri, yükseltmeleri kontrol ediyoruz, sondaki -y işareti gelen onay işlemlerini otamatik olarak onaylanmasını sağlayacaktır.
 
```
ufw allow 22 && ufw allow 3000
ufw enable
```

  ```
 sudo apt-get update && sudo apt-get upgrade -y
  ```

 ## Bu komut ile bize gerekli olan dependencies ları indiriyoruz: Bağımlılık (dependency) kurulumda ihtiyaç duyduğumuz dışarıdan eklediğimiz kaynaklar ya da bileşenlerdir (kütüphane).

 ```
sudo apt install curl git build-essential 
 ```
   ```
sudo apt install yarn
   ```
  ## Bizden istenilen özelliklere uygun olarak node js kuruyoruz
   ```
sudo apt-get install nodejs
 ```
```
sudo apt install npm
```
 ## versiyonları kontrol ediyoruz çıktıda 16 üstü değilse yükseltme yapamamız gerekiyor örnek olara versiyon cıktısı 10 ile başlıyorsa 10. versiyon kurulu, bu yüzden yükseltme gerekiyor.
```
nodejs -v
```

```
npm -v
```
 
  
   ## Yükseltme gerekiyorsa burdaki komutları ekleyip 18'e yükseltebilirsiniz.
   
   ```
   curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```
   ```
sudo apt-get install nodejs
```
# Versiyonları kontrol edelim. versiyon çıktısı node için 18 ile başlarsa sorun yok.

```
node -v
```

```
npm -v
```
   ```
  git clone https://github.com/o1-labs/zkapp-cli
   ```
   ```
  npm instal -g zkapp-cli@0.5.3
   ```
  ```
  zk --version
   ```

## Zkapp kurulumu:
  
  ```
  npm install -g zkapp-cli
  ```
# Alttaki komutları kendinize göre düzenleyip devam edin Email adresinizi ve isim yazın.

```
git config --global user.email (mail adresiniz)
```
  
```
git config --global user.name (kullanıcı ismi)
  
```
  
  # Proje oluşturma
  ## Altakki komutu yazdıktan sonra gelen 2 işlemide klavyedeki yön tuşlarıyla yes diyip enter tuşuyla onaylıyoruz 3. seçenekte yine y tuşuna basıp enter dedikten sonra yes seçeneğini seçiyoruz.
  
  ```
  zk project 04-zkapp-browser-ui --ui next
  ```
  - Bu adımda github profilimzde ``` 04-zkapp-browser-ui ``` adında bir repo oluşturacağız. Repo oluşturmayı videoda görebilirsiniz.
  - daha sonra ``` settting ``` kısmından 
-  ``` developer setting ```  kısmını seçiyoruz
- ``` personal access token ```  ardında ``` choose token(classis) ``` seçiyoruz.
bize verdiği şifreyi kaydedelim. ilerleyen süreçlerde kullanacağız.
  ```
  cd 04-zkapp-browser-ui
  ```
  ```
  git remote add origin oluşturduğumuz repo'nun url adresi
  ```
  ```
  git push -u origin main
  ```
  contrat çalıştırıyoruz
  
 ```
cd
cd 04-zkapp-browser-ui/contracts/
 ```
```
npm run build
  ```
  dizin değiştirip
 
  ```
  cd
cd 04-zkapp-browser-ui/ui/pages
  ```
  alttaki kodu yazdıktan sonra diğer komutun tamamını kopyalayıp yapıştırın.
  ```
  sudo nano zkappWorker.ts
```
 ```
 import {
    Mina,
    isReady,
    PublicKey,
    PrivateKey,
    Field,
    fetchAccount,
} from 'snarkyjs'

type Transaction = Awaited<ReturnType<typeof Mina.transaction>>;

// ---------------------------------------------------------------------------------------

import type { Add } from '../../contracts/src/Add';

const state = {
    Add: null as null | typeof Add,
    zkapp: null as null | Add,
    transaction: null as null | Transaction,
}

// ---------------------------------------------------------------------------------------

const functions = {
    loadSnarkyJS: async (args: {}) => {
        await isReady;
    },
    setActiveInstanceToBerkeley: async (args: {}) => {
        const Berkeley = Mina.BerkeleyQANet(
            "https://proxy.berkeley.minaexplorer.com/graphql"
        );
        Mina.setActiveInstance(Berkeley);
    },
    loadContract: async (args: {}) => {
        const { Add } = await import('../../contracts/build/src/Add.js');
        state.Add = Add;
    },
    compileContract: async (args: {}) => {
        await state.Add!.compile();
    },
    fetchAccount: async (args: { publicKey58: string }) => {
        const publicKey = PublicKey.fromBase58(args.publicKey58);
        return await fetchAccount({ publicKey });
    },
    initZkappInstance: async (args: { publicKey58: string }) => {
        const publicKey = PublicKey.fromBase58(args.publicKey58);
        state.zkapp = new state.Add!(publicKey);
    },
    getNum: async (args: {}) => {
        const currentNum = await state.zkapp!.num.get();
        return JSON.stringify(currentNum.toJSON());
    },
    createUpdateTransaction: async (args: {}) => {
        const transaction = await Mina.transaction(() => {
            state.zkapp!.update();
        }
        );
        state.transaction = transaction;
    },
    proveUpdateTransaction: async (args: {}) => {
        await state.transaction!.prove();
    },
    getTransactionJSON: async (args: {}) => {
        return state.transaction!.toJSON();
    },
};

// ---------------------------------------------------------------------------------------

export type WorkerFunctions = keyof typeof functions;

export type ZkappWorkerRequest = {
    id: number,
    fn: WorkerFunctions,
    args: any
}

export type ZkappWorkerReponse = {
    id: number,
    data: any
}
if (process.browser) {
    addEventListener('message', async (event: MessageEvent<ZkappWorkerRequest>) => {
        const returnData = await functions[event.data.fn](event.data.args);

        const message: ZkappWorkerReponse = {
            id: event.data.id,
            data: returnData,
        }
        postMessage(message)
    });
}
 ```
 ctrl x ile çıkıyoruz y yazıp enter diyoruz.
 
 2. dosyayı düzenliyoruz
  ```
sudo nano zkappWorkerClient.ts
  ```
 ```
 import {
    fetchAccount,
    PublicKey,
    PrivateKey,
    Field,
} from 'snarkyjs'

import type { ZkappWorkerRequest, ZkappWorkerReponse, WorkerFunctions } from './zkappWorker';

export default class ZkappWorkerClient {

    // ---------------------------------------------------------------------------------------

    loadSnarkyJS() {
        return this._call('loadSnarkyJS', {});
    }

    setActiveInstanceToBerkeley() {
        return this._call('setActiveInstanceToBerkeley', {});
    }

    loadContract() {
        return this._call('loadContract', {});
    }

    compileContract() {
        return this._call('compileContract', {});
    }

    fetchAccount({ publicKey }: { publicKey: PublicKey }): ReturnType<typeof fetchAccount> {
        const result = this._call('fetchAccount', { publicKey58: publicKey.toBase58() });
        return (result as ReturnType<typeof fetchAccount>);
    }

    initZkappInstance(publicKey: PublicKey) {
        return this._call('initZkappInstance', { publicKey58: publicKey.toBase58() });
    }

    async getNum(): Promise<Field> {
        const result = await this._call('getNum', {});
        return Field.fromJSON(JSON.parse(result as string));
    }

    createUpdateTransaction() {
        return this._call('createUpdateTransaction', {});
    }

    proveUpdateTransaction() {
        return this._call('proveUpdateTransaction', {});
    }

    async getTransactionJSON() {
        const result = await this._call('getTransactionJSON', {});
        return result;
    }

    // ---------------------------------------------------------------------------------------

    worker: Worker;

    promises: { [id: number]: { resolve: (res: any) => void, reject: (err: any) => void } };

    nextId: number;

    constructor() {
        this.worker = new Worker(new URL('./zkappWorker.ts', import.meta.url))
        this.promises = {};
        this.nextId = 0;

        this.worker.onmessage = (event: MessageEvent<ZkappWorkerReponse>) => {
            this.promises[event.data.id].resolve(event.data.data);
            delete this.promises[event.data.id];
        };
    }

    _call(fn: WorkerFunctions, args: any) {
        return new Promise((resolve, reject) => {
            this.promises[this.nextId] = { resolve, reject }

            const message: ZkappWorkerRequest = {
                id: this.nextId,
                fn,
                args,
            };

            this.worker.postMessage(message);

            this.nextId++;
        });
    }
}
 ```
 
 

  

  
  
