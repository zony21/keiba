# 小倉記念 使用資料

このフォルダには採点の根拠となるUTF-8テキスト、Markdown、CSVを保存する。

## 推奨ファイル
- `race_info.md`：競馬場、距離、回り、コース、クラス、ハンデ条件、想定馬場
- `entry_list.csv`：馬番、馬名、年齢、性別、斤量、騎手
- `past_5_races.csv`：全出走馬の過去5走
- `additional_records.csv`：コース・距離など過去5走外の補足実績

## past_5_races.csv 必須項目
`horse_no,horse_name,race_order,date,racecourse,distance,surface,turn,weather,track_condition,class,field_size,weight,jockey,finish,margin,popularity,corner_order,final_3f,final_3f_rank,winner,pace`

未取得項目は空欄にし、推測値を入れない。
