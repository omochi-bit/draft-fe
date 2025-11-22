# テーブル定義書（Based on ERD）

## 1. `users` テーブル

### 概要

ユーザー情報を管理するテーブル。

### カラム定義

  カラム名        型         NOT NULL   主キー   UNIQUE   説明
  --------------- ---------- ---------- -------- -------- --------------------
  id              UUID       YES        PK       \-       ユーザーID
  email           string     YES        \-       UNIQUE   メールアドレス
  password_hash   string     YES        \-       \-       パスワードハッシュ
  created_at      datetime   YES        \-       \-       作成日時
  updated_at      datetime   YES        \-       \-       更新日時

### インデックス

  名称                 カラム   ユニーク
  -------------------- -------- ----------
  users_email_unique   email    YES

------------------------------------------------------------------------

## 2. `tasks` テーブル

### 概要

ユーザーのタスクを管理するテーブル。

### カラム定義

  カラム名       型         NOT NULL   主キー   UNIQUE   説明
  -------------- ---------- ---------- -------- -------- ----------------
  id             UUID       YES        PK       \-       タスクID
  user_id        UUID       YES        FK       \-       作成ユーザーID
  title          string     YES        \-       \-       タイトル
  description    string     NO         \-       \-       詳細
  is_completed   boolean    YES        \-       \-       完了フラグ
  created_at     datetime   YES        \-       \-       作成日時
  updated_at     datetime   YES        \-       \-       更新日時

### インデックス

  名称                       カラム         ユニーク
  -------------------------- -------------- ----------
  tasks_user_id_index        user_id        NO
  tasks_is_completed_index   is_completed   NO

### 外部キー

  名称               参照先      カラム
  ------------------ ----------- ---------
  tasks_user_id_fk   users(id)   user_id

------------------------------------------------------------------------

## 3. `tags` テーブル

### 概要

ユーザーごとのタグを管理するテーブル。

### カラム定義

  カラム名     型         NOT NULL   主キー            UNIQUE   説明
  ------------ ---------- ---------- ----------------- -------- ------------
  id           UUID       YES        PK                \-       タグID
  user_id      UUID       YES        FK                \-       ユーザーID
  name         string     YES        UNIQUE per user   \-       タグ名
  created_at   datetime   YES        \-                \-       作成日時
  updated_at   datetime   YES        \-                \-       更新日時

### インデックス

  名称                 カラム    ユニーク
  -------------------- --------- ----------
  tags_user_id_index   user_id   NO
  tags_name_index      name      NO

### 複合一意制約

  名称                       カラム
  -------------------------- -----------------
  tags_user_id_name_unique   (user_id, name)

### 外部キー

  名称              参照先      カラム
  ----------------- ----------- ---------
  tags_user_id_fk   users(id)   user_id

------------------------------------------------------------------------

## 4. `task_tags` テーブル

### 概要

タスクとタグの多対多関係を表す中間テーブル。

### カラム定義

  カラム名   型     NOT NULL   主キー           説明
  ---------- ------ ---------- ---------------- ----------
  task_id    UUID   YES        PK (composite)   タスクID
  tag_id     UUID   YES        PK (composite)   タグID

### 外部キー

  名称                   参照先      カラム
  ---------------------- ----------- ---------
  task_tags_task_id_fk   tasks(id)   task_id
  task_tags_tag_id_fk    tags(id)    tag_id
