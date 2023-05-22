テーブル：channels

| カラム名 | データ型 | NULL | キー | 初期値 | AUTO INCREMENT |
| --- | --- | --- | --- | --- | --- |
| id | INT |  | PRIMARY |  | YES |
| name | VARCHAR(255) |  | UNIQUE |  |  |

テーブル：programs

| カラム名 | データ型 | NULL | キー | 初期値 | AUTO INCREMENT |
| --- | --- | --- | --- | --- | --- |
| id | INT |  | PRIMARY |  | YES |
| title | VARCHAR(255) |  |  |  |  |
| description | TEXT | YES |  |  |  |

テーブル：seasons

| カラム名 | データ型 | NULL | キー | 初期値 | AUTO INCREMENT |
| --- | --- | --- | --- | --- | --- |
| id | INT |  | PRIMARY |  | YES |
| program_id | INT |  | FOREIGN |  |  |
| season | INT | YES |  |  |  |

外部キー制約：

- program_idはprogramsテーブルのidを参照

テーブル：episodes

| カラム名 | データ型 | NULL | キー | 初期値 | AUTO INCREMENT |
| --- | --- | --- | --- | --- | --- |
| id | INT |  | PRIMARY |  | YES |
| season_id | INT | YES | FOREIGN |  |  |
| title | VARCHAR(255) |  |  |  |  |
| description | TEXT | YES |  |  |  |
| duration | INT |  |  |  |  |
| air_date | DATE |  |  |  |  |
| episode | INT | YES |  | 0 |  |

外部キー制約：

- season_idはseasonsテーブルのidを参照

テーブル：genres

| カラム名 | データ型 | NULL | キー | 初期値 | AUTO INCREMENT |
| --- | --- | --- | --- | --- | --- |
| id | INT |  | PRIMARY |  | YES |
| name | VARCHAR(255) |  | UNIQUE |  |  |

テーブル：programs_genres

| カラム名 | データ型 | NULL | キー | 初期値 | AUTO INCREMENT |
| --- | --- | --- | --- | --- | --- |
| id | INT |  | PRIMARY |  | YES |
| genre_id | INT |  | FOREIGN |  |  |
| program_id | INT |  | FOREIGN |  |  |

外部キー制約：

- genre_idはgenresテーブルのidを参照
- program_idはprogramsテーブルのidを参照

テーブル：channel_programs

| カラム名 | データ型 | NULL | キー | 初期値 | AUTO INCREMENT |
| --- | --- | --- | --- | --- | --- |
| id | INT |  | PRIMARY |  | YES |
| channel_id | INT |  | FOREIGN |  |  |
| program_id | INT |  | FOREIGN |  |  |
| start_time | DATETIME |  |  |  |  |
| end_time | DATETIME |  |  |  |  |
| is _repeat | BOOL |  |  | FALSE |  |

外部キー制約：

- channel_idはchannelsテーブルのidを参照
- program_idはprogramsテーブルのidを参照

テーブル：view_counts

| カラム名 | データ型 | NULL | キー | 初期値 | AUTO INCREMENT |
| --- | --- | --- | --- | --- | --- |
| id | INT |  | PRIMARY |  | YES |
| channel_program_id | INT |  | FOREIGN |  |  |
| episode_id | INT |  | FOREIGN |  |  |
| views | INT |  |  | 0 |  |

外部キー制約：

- channel_program_idはchannel_programsテーブルのidを参照
- episode_idはepisodesテーブルのidを参照
