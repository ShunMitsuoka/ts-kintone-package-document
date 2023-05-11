## 現在のアプリを取得する。

```JS
const kintoneAppRepository = new KintoneAppRepository()
const currentApp : KintoneApp = await kintoneAppRepository.getCurrentApp();
```

## 現在のアプリの全フィールドを取得する。

### KintoneFields形式
```JS
const kintoneAppRepository = new KintoneAppRepository()
const currentApp : KintoneApp = await kintoneAppRepository.getCurrentApp();
const fields : KintoneFields = currentApp.getFields();
```

### Map<string, KintoneField>形式
```JS
const kintoneAppRepository = new KintoneAppRepository()
const currentApp : KintoneApp = await kintoneAppRepository.getCurrentApp();
const fields : Map<string, KintoneField> = currentApp.getFieldsMap();
```

## フィールドの各種情報を取得する。
```JS
const fields : KintoneFields = currentApp.getFields();
const field : KintoneField = fields.getField('フィールドコード1');
// フィールドコード取得
field.getFieldCode();
// フィールド名取得
field.getFieldProperties().getLabel();
// フィールドタイプ取得
field.getFieldProperties().getType().type;
// 必須項目かどうか
field.getFieldProperties().required
// 初期値取得
field.getFieldProperties().defaultValue
```

## 現在のアプリの全レコードを取得する。

```JS
const kintoneAppRepo = new KintoneAppRepository();
const kintoneRecordRepo = new KintoneRecordRepository();
const currentApp : KintoneApp = await kintoneAppRepo.getCurrentApp();
const records : KintoneRecord[] = await kintoneRecordRepo.getAll(currentApp.getAppId());
```

## 現在開いている一覧の絞り込み条件を使用してレコードを抽出する。

```JS
const kintoneAppRepo = new KintoneAppRepository();
const kintoneViewRepo = new KintoneViewRepository();
const kintoneRecordRepo = new KintoneRecordRepository();
const currentApp : KintoneApp  = await kintoneAppRepo.getCurrentApp();
const views : KintoneViews = await kintoneViewRepo.getAll(currentApp.getAppId());
const currentView : KintoneView = views.getView(viewId.id);
const records : KintoneRecord[] = await kintoneRecordRepo.getAll(currentApp.getAppId(), currentView.makeQuery());
```

## 現在のアプリにレコードを追加する。

```JS
let newRecords: KintoneRecord[] = [];
const kintoneAppRepo = new KintoneAppRepository();
const kintoneRecordRepo = new KintoneRecordRepository();
const currentAppId = kintoneAppRepo.getCurrentAppId();
const newRecord : KintoneRecord[] = currentApp.newRecord();
// 'フィールドコード1'というフィールドに値'テスト'を設定
newRecord.setValue('フィールドコード1', 'テスト');
newRecords.push(newRecord);
// レコード追加
const result = await this.kintoneRecordRepository.createAll(currentAppId, newRecords);
```
