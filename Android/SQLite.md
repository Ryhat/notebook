# SQL Lite

## 准备工作

## 创建contract类

### 在contract类中创建内部类Entry

```java
public class UserContract {
    public static final class UserEntry implements BaseColumns{
        public static final String TABLE_NAME = "user";
        public static final String COLUMN_USERNAME = "username";
        public static final String COLUMN_USER_ID = "user_id";
        public static final String COLUMN_REAL_NAME = "real_name";
        public static final String COLUMN_SEX = "sex";
        public static final String COLUMN_BIRTHDAY = "birthday";
        public static final String COLUMN_ADDRESS = "address";
        public static final String COLUMN_EMERGENCY_PEOPLE = "emergency_people";
        public static final String COLUMN_EMERGENCY_TEL = "emergency_tel";
        public static final String COLUMN_TELEPHONE = "telephone";
    }
}
```

### 创建DBHelper类

#### 初始化必要变量

```java
private static final String TAG = "DBHelper";
private static final String DATABASE_NAME = "alarm_user.db";
private static final int DATABASE_VERSION = 2;
```

#### 构造函数

```java
public DBHelper(@Nullable Context context) {
    super(context, DATABASE_NAME, null, DATABASE_VERSION);
}
```

#### onCreate

```java
@Override
    public void onCreate(SQLiteDatabase db) {
        final String SQL_CREATE_USER_TABLE =
                "CREATE TABLE " + UserContract.UserEntry.TABLE_NAME + "(" +
                        UserContract.UserEntry.COLUMN_USERNAME + " TEXT PRIMARY KEY," +
                        UserContract.UserEntry.COLUMN_USER_ID + " TEXT,"+
                        UserContract.UserEntry.COLUMN_REAL_NAME + " TEXT,"+
                        UserContract.UserEntry.COLUMN_SEX + " TEXT,"+
                        UserContract.UserEntry.COLUMN_BIRTHDAY + " TEXT,"+
                        UserContract.UserEntry.COLUMN_ADDRESS + " TEXT,"+
                        UserContract.UserEntry.COLUMN_EMERGENCY_PEOPLE + " TEXT,"+
                        UserContract.UserEntry.COLUMN_TELEPHONE + " TEXT," +
                        UserContract.UserEntry.COLUMN_EMERGENCY_TEL + " TEXT)";
        Log.d(TAG, "onCreate: " + SQL_CREATE_USER_TABLE);

        db.execSQL(SQL_CREATE_USER_TABLE);
    }
```

#### onUpgrade

```java
@Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        db.execSQL("DROP TABLE IF EXISTS "+ UserContract.UserEntry.TABLE_NAME);
        onCreate(db);
    }
```

#### 总览

```java
public class DBHelper extends SQLiteOpenHelper {

    private static final String TAG = "DBHelper";

    private static final String DATABASE_NAME = "alarm_user.db";

    private static final int DATABASE_VERSION = 2;

    public DBHelper(@Nullable Context context) {
        super(context, DATABASE_NAME, null, DATABASE_VERSION);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        final String SQL_CREATE_USER_TABLE =
                "CREATE TABLE " + UserContract.UserEntry.TABLE_NAME + "(" +
                        UserContract.UserEntry.COLUMN_USERNAME + " TEXT PRIMARY KEY," +
                        UserContract.UserEntry.COLUMN_USER_ID + " TEXT,"+
                        UserContract.UserEntry.COLUMN_REAL_NAME + " TEXT,"+
                        UserContract.UserEntry.COLUMN_SEX + " TEXT,"+
                        UserContract.UserEntry.COLUMN_BIRTHDAY + " TEXT,"+
                        UserContract.UserEntry.COLUMN_ADDRESS + " TEXT,"+
                        UserContract.UserEntry.COLUMN_EMERGENCY_PEOPLE + " TEXT,"+
                        UserContract.UserEntry.COLUMN_TELEPHONE + " TEXT," +
                        UserContract.UserEntry.COLUMN_EMERGENCY_TEL + " TEXT)";
        Log.d(TAG, "onCreate: " + SQL_CREATE_USER_TABLE);

        db.execSQL(SQL_CREATE_USER_TABLE);
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        db.execSQL("DROP TABLE IF EXISTS "+ UserContract.UserEntry.TABLE_NAME);
        onCreate(db);
    }
}
```

## 使用

### 创建实例

```java

```

### 增

### 删

### 查

### 改