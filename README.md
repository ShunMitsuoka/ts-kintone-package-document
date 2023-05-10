#  「ts-kintone-package」公式ドキュメント

本ドキュメントは「[ts-kintone-package](https://github.com/ShunMitsuoka/ts-kintone-package)」の公式ドキュメントです。  
個人で開発を行っているため、ドキュメントの整備は少しずつ行っていきますのでご了承下さい。
  
本ライブラリは以下の層から成り立ちます。  
* Infrastructure層  
* Application層  
* Domain層  
  
ライブラリを使用時にメインで使用することになるのは  
* Domain層のModels  
* Infrastructure層のRepository  
です。

## Domain層のModelsについて

Domain層のModelsには例えば、1つのアプリを表す**KintoneApp**が存在します。  
そして、**KintoneApp**はそのアプリに存在するフィールドを表す**KintoneFields**を持っています。

アプリの全フィールドを取得する場合には以下のように使用します。
```JS
const fields : KintoneFields = kintoneApp.getFields();
```

アプリの任意のフィールドを取得する場合は以下のように使用します。
```JS
const fields : KintoneFields = kintoneApp.getFields();
const field : KintoneField = fields.getField('フィールドコード1');
```

## Infrastructure層のRepositoryについて

実際にkintoneのカスタマイズやプラグインの開発を行っていく場合、  
まずは、現在のアプリの情報を取得する必要がある場合が多いです。

本ライブラリでは以下のようなコードで、現在のアプリの情報を取得することが可能です。

```JS
const kintoneAppRepository = new KintoneAppRepository()
const currentApp : KintoneApp = await kintoneAppRepository.getCurrentApp();
```

上記で取得した**currentApp**には、アプリIDだけでなく、全フィールドの情報なども既に設定されています。  
従って、現在のアプリに"商品コード"というフィールドコードのフィールドが存在するか確認したい場合は以下のようなコードで実現できます。

```JS
const kintoneAppRepository = new KintoneAppRepository()
const currentApp : KintoneApp = await kintoneAppRepository.getCurrentApp();
if(currentApp.existsFieldCode('商品コード')){
    // "商品コード"というフィールドコードのフィールドが存在した場合の処理
}
```

例えば、現在のアプリの全フィールドを取得して、セレクトボックスを作成したい場合は以下のようなコードで実現できます。

```JS
const kintoneAppRepository = new KintoneAppRepository()
const currentApp : KintoneApp = await kintoneAppRepository.getCurrentApp();
const fields : Map<string, KintoneField> = currentApp.getFieldsMap();
let options = [];
fields.forEach(field => {
    const fieldCode = field.getFieldCode();
    const label = field.getFieldProperties().label;
    // 以下はイメージです。
    // optionsへの追加方法は生のJavaScriptなのか、jQueryなのか、Reactなのか等で変わってきます。
    options.push('<option value="'+fieldCode+'">'+label+'</option>')
});
```
