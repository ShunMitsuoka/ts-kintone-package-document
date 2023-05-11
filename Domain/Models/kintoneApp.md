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
| setFields(fields : KintoneFields) | フィールドを設定する |
| concatFields(addFields : KintoneFields) | フィールドを追加する |
| getFields() | フィールドを取得する |
| getFieldsMap() | フィールドをMap形式で取得する |
| getCustomFields() | カスタムフィールドを取得する |
| existsFieldCode(fieldCode : KintoneFieldCode) | フィールドコードに一致するフィールドが存在するか判定する |
| newRecord(recordId?: KintoneRecordId) | 新しいレコードを作成する |
| isThisAppId(targetAppId : AppId) | 引数のAppIdが自アプリかどうか判定する |

### `setAppId(appId:AppId)`
アプリIDを設定する。  
※既にアプリIDが設定されている場合はエラーになります。
* 引数

|  変数名  |  型  | デフォルト | 必須 | 説明 |
| ---- | ---- | ---- | ---- | ---- |
|  `appId`  | AppId |  | 必須 | 設定するAppId |

* 戻り値　：　`なし`

### `getAppId()`
アプリIDを設定する。  
※既にアプリIDが設定されていない場合はエラーになります。
* 引数　：　`なし`

* 戻り値　：　`AppId`

### `setRevision(revision : number)`
リビジョンを設定する。  
* 引数

|  変数名  |  型  | デフォルト | 必須 | 説明 |
| ---- | ---- | ---- | ---- | ---- |
|  `revision`  | number |  | 必須 | 設定するリビジョン番号 |

* 戻り値　：　`なし`

### `getRevision()`
リビジョンを取得する。  
* 引数　：　`なし`

* 戻り値　：　`number | undefined`

### `setFields(fields : KintoneFields)`
フィールドを設定する。  
* 引数

|  変数名  |  型  | デフォルト | 必須 | 説明 |
| ---- | ---- | ---- | ---- | ---- |
|  `fields`  | KintoneFields |  | 必須 | 設定するフィールド情報 |

* 戻り値　：　`なし`

### `concatFields(addFields : KintoneFields)`
既にアプリに設定されているフィールドに対して、新たなフィールドを追加します。
* 引数

|  変数名  |  型  | デフォルト | 必須 | 説明 |
| ---- | ---- | ---- | ---- | ---- |
|  `addFields`  | KintoneFields |  | 必須 | 新たに追加するフィールド情報 |

* 戻り値　：　`なし`

### `getFields()`
フィールドを取得する。  
* 引数　：　`なし`

* 戻り値　：　`KintoneFields`

### `getFieldsMap()`
フィールドをMap形式で取得する。  
`KintoneFields`が内部に持つ`Map<string, KintoneField>`を直接取得します。  
Mapのキー(string)はフィールドコードになります。
* 引数　：　`なし`

* 戻り値　：　`Map<string, KintoneField>`

### `getCustomFields()`
kintoneアプリがデフォルトで持つフィールドを除いたユーザーが追加したフィールドを取得します。
* 引数　：　`なし`

* 戻り値　：　`Map<string, KintoneField>`

### `existsFieldCode(fieldCode : KintoneFieldCode)`
対象のアプリ上に引数で渡したフィールドコードが存在するかどうか判定します。
* 引数  

|  変数名  |  型  | デフォルト | 必須 | 説明 |
| ---- | ---- | ---- | ---- | ---- |
|  `fieldCode`  | KintoneFieldCode |  | 必須 | 存在を確認するフィールドコード |

* 戻り値　：　`boolean`

### `newRecord(recordId?: KintoneRecordId)`
対象のアプリのフィールド情報から新規レコードを作成します。
* 引数  

|  変数名  |  型  | デフォルト | 必須 | 説明 |
| ---- | ---- | ---- | ---- | ---- |
|  `recordId`  | KintoneRecordId |  | 省略可 | 新規レコードに設定するレコードID |

* 戻り値　：　`KintoneRecord`