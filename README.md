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
 ```
cd
 ```
  ```
cd 04-zkapp-browser-ui/ui/styles
 ```
 ```
 sudo nano globals.css
 ```
 ```
 html,
body {
  padding: 0;
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen,
    Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
}

a {
  color: inherit;
  text-decoration: none;
}

* {
  box-sizing: border-box;
}

@media (prefers-color-scheme: dark) {
  html {
    color-scheme: dark;
  }
  body {
    color: white;
    background: black;
  }
}
 
```

```
cd
```
```
cd 04-zkapp-browser-ui/ui/
```
```
npm run dev
```
2 adet yeni sekme açalım giriş yapalım daha sonra sırasıyla şalttaki komutları çalıştıralım.
1. sekme
```
cd
cd 04-zkapp-browser-ui/ui/
npm run dev
```
2.sekme
```
cd
cd 04-zkapp-browser-ui/ui/pages
sudo nano _app.page.tsx
```
  daha sonra tarayıcımıza ıp:3000 yazarak kontrol edelim ıp burda sizin kendi ip niz olacak https kısmı silinecek.
  ```
  cd
cd 04-zkapp-browser-ui/ui/pages
sudo nano _app.page.tsx
```
```
// import '../styles/globals.css'
// import type { AppProps } from 'next/app'

// import './reactCOIServiceWorker';

// export default function App({ Component, pageProps }: AppProps) {
//   return <Component {...pageProps} />
// }


import '../styles/globals.css'
import { useEffect, useState } from "react";
import './reactCOIServiceWorker';

import ZkappWorkerClient from './zkappWorkerClient';

import {
  PublicKey,
  PrivateKey,
  Field,
} from 'snarkyjs'

let transactionFee = 0.1;

export default function App() {

  let [state, setState] = useState({
    zkappWorkerClient: null as null | ZkappWorkerClient,
    hasWallet: null as null | boolean,
    hasBeenSetup: false,
    accountExists: false,
    currentNum: null as null | Field,
    publicKey: null as null | PublicKey,
    zkappPublicKey: null as null | PublicKey,
    creatingTransaction: false,
  });

  // -------------------------------------------------------
  // Do Setup

  useEffect(() => {
    (async () => {
      if (!state.hasBeenSetup) {
        const zkappWorkerClient = new ZkappWorkerClient();

        console.log('Loading SnarkyJS...');
        await zkappWorkerClient.loadSnarkyJS();
        console.log('done');

        await zkappWorkerClient.setActiveInstanceToBerkeley();

        const mina = (window as any).mina;

        if (mina == null) {
          setState({ ...state, hasWallet: false });
          return;
        }

        const publicKeyBase58: string = (await mina.requestAccounts())[0];
        const publicKey = PublicKey.fromBase58(publicKeyBase58);

        console.log('using key', publicKey.toBase58());

        console.log('checking if account exists...');
        const res = await zkappWorkerClient.fetchAccount({ publicKey: publicKey! });
        const accountExists = res.error == null;

        await zkappWorkerClient.loadContract();

        console.log('compiling zkApp');
        await zkappWorkerClient.compileContract();
        console.log('zkApp compiled');

        const zkappPublicKey = PublicKey.fromBase58('B62qrDe16LotjQhPRMwG12xZ8Yf5ES8ehNzZ25toJV28tE9FmeGq23A');

        await zkappWorkerClient.initZkappInstance(zkappPublicKey);

        console.log('getting zkApp state...');
        await zkappWorkerClient.fetchAccount({ publicKey: zkappPublicKey })
        const currentNum = await zkappWorkerClient.getNum();
        console.log('current state:', currentNum.toString());

        setState({
          ...state,
          zkappWorkerClient,
          hasWallet: true,
          hasBeenSetup: true,
          publicKey,
          zkappPublicKey,
          accountExists,
          currentNum
        });
      }
    })();
  }, []);

  // -------------------------------------------------------
  // Wait for account to exist, if it didn't

  useEffect(() => {
    (async () => {
      if (state.hasBeenSetup && !state.accountExists) {
        for (; ;) {
          console.log('checking if account exists...');
          const res = await state.zkappWorkerClient!.fetchAccount({ publicKey: state.publicKey! })
          const accountExists = res.error == null;
          if (accountExists) {
            break;
          }
          await new Promise((resolve) => setTimeout(resolve, 5000));
        }
        setState({ ...state, accountExists: true });
      }
    })();
  }, [state.hasBeenSetup]);

  // -------------------------------------------------------
  // Send a transaction

  const onSendTransaction = async () => {
    setState({ ...state, creatingTransaction: true });
    console.log('sending a transaction...');

    await state.zkappWorkerClient!.fetchAccount({ publicKey: state.publicKey! });

    await state.zkappWorkerClient!.createUpdateTransaction();

    console.log('creating proof...');
    await state.zkappWorkerClient!.proveUpdateTransaction();

    console.log('getting Transaction JSON...');
    const transactionJSON = await state.zkappWorkerClient!.getTransactionJSON()

    console.log('requesting send transaction...');
    const { hash } = await (window as any).mina.sendTransaction({
      transaction: transactionJSON,
      feePayer: {
        fee: transactionFee,
        memo: '',
      },
    });

    console.log(
      'See transaction at https://berkeley.minaexplorer.com/transaction/' + hash
    );

    setState({ ...state, creatingTransaction: false });
  }

  // -------------------------------------------------------
  // Refresh the current state

  const onRefreshCurrentNum = async () => {
    console.log('getting zkApp state...');
    await state.zkappWorkerClient!.fetchAccount({ publicKey: state.zkappPublicKey! })
    const currentNum = await state.zkappWorkerClient!.getNum();
    console.log('current state:', currentNum.toString());

    setState({ ...state, currentNum });
  }

  // -------------------------------------------------------
  // Create UI elements

  let hasWallet;
  if (state.hasWallet != null && !state.hasWallet) {
    const auroLink = 'https://www.aurowallet.com/';
    const auroLinkElem = <a href={auroLink} target="_blank" rel="noreferrer"> [Link] </a>
    hasWallet = <div> Could not find a wallet. Install Auro wallet here: {auroLinkElem}</div>
  }

  let setupText = state.hasBeenSetup ? 'SnarkyJS Ready' : 'Setting up SnarkyJS...';
  let setup = <div> {setupText} {hasWallet}</div>

  let accountDoesNotExist;
  if (state.hasBeenSetup && !state.accountExists) {
    const faucetLink = "https://faucet.minaprotocol.com/?address=" + state.publicKey!.toBase58();
    accountDoesNotExist = <div>
      Account does not exist. Please visit the faucet to fund this account
      <a href={faucetLink} target="_blank" rel="noreferrer"> [Link] </a>
    </div>
  }

  let mainContent;
  if (state.hasBeenSetup && state.accountExists) {
    mainContent = <div>
      <button onClick={onSendTransaction} disabled={state.creatingTransaction}> Send Transaction </button>
      <div> Current Number in zkApp: {state.currentNum!.toString()} </div>
      <button onClick={onRefreshCurrentNum}> Get Latest State </button>
    </div>
  }

  return <div>
    {setup}
    {accountDoesNotExist}
    {mainContent}
  </div>
}
```



  
  
