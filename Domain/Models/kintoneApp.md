# アプリ関連

|  オブジェクト  |  説明  |
| ---- | ---- |
|  [AppId](#AppId)  |  kintoneアプリId |
|  [KintoneApp](#KintoneApp)  |  kintoneアプリ |
|  KintoneDeployStatus  |  kintoneアプリ更新状態 |

## AppId
kintoneのアプリID
### Properties

| Name | Type | Access Modifiers | 説明 |
| ---- | ---- | ---- | ---- |
| id | number | readonly | Kintone App ID |

## KintoneApp

kintoneアプリ

### Properties

| Name | Type | Access Modifiers | 説明 |
| ---- | ---- | ---- | ---- |
| _appId | number | private | Kintone App ID |
| appName | string | readonly | Kintone App Name |
| space | number | readonly | Kintone App space |
| thread | number | readonly | Kintone App thread |
| revision | number | private | Kintone App revision |
| fields | KintoneFields | private | Kintone Fields |

### Methods

| Name | 説明 |
| ---- | ---- |
| setAppId(appId:AppId) | アプリIDを設定する |
| getAppId() | アプリIDを取得する |
| setRevision(revision : number) | リビジョンを設定する |
| getRevision() | リビジョンを取得する |
| isThisAppId(targetAppId : AppId) | 引数のAppIdが自アプリかどうか判定する |
| setFields(fields : KintoneFields) | フィールドを設定する |
| concatFields(addFields : KintoneFields) | フィールドを追加する |
| getFields() | フィールドを取得する |
| getFieldsMap() | フィールドをMap形式で取得する |
| getCustomFields() | カスタムフィールドを取得する |
| existsFieldCode(fieldCode : KintoneFieldCode) | フィールドコードに一致するフィールドが存在するか判定する |
| newRecord(recordId?: KintoneRecordId) | 新しいレコードを作成する |

### `setAppId(appId:AppId)`
アプリIDを設定する。  
※既にアプリIDが設定されている場合はエラーになります。
* 引数

|  変数名  |  型  | デフォルト| 説明 |
| ---- | ---- | ---- | ---- |
|  `appId`  | AppId |  | 設定するAppId |

* 戻り値　：　`なし`

