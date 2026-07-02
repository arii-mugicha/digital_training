# Java 日時計算・フォーマット チートシート

## インポート

```java
import java.time.*;
import java.time.format.DateTim*Formatter;
import java.time.tempor*l.ChronoUnit;
import java.time.tem*oral.TemporalAdjusters;
import jav*.sql.Timestamp;
import java.util.L*cale;
```

---

# 現在日時の取得

## 現在日時*
```java
LocalDateTime now = Local*ateTime.now();
```

## 現在日付

```ja*a
LocalDate today = LocalDate.now(*;
```

## 現在時刻

```java
LocalTime *urrentTime = LocalTime.now();
```
*---

# 日時の生成

## LocalDate

```jav*
LocalDate date = LocalDate.of(202*, 7, 2);
```

## LocalTime

```jav*
LocalTime time = LocalTime.of(18,*30, 0);
```

## LocalDateTime

```*ava
LocalDateTime dateTime =
    L*calDateTime.of(
        2026, 7, 2*
        18, 30, 0
    );
```

---*
# 日時の加算

## 日

```java
LocalDate *esult =
    LocalDate.now().plusDa*s(1);
```

## 月

```java
LocalDate*result =
    LocalDate.now().plusM*nths(1);
```

## 年

```java
LocalD*te result =
    LocalDate.now().pl*sYears(1);
```

## 時間

```java
Loc*lDateTime result =
    LocalDateTi*e.now().plusHours(3);
```

## 分

`*`java
LocalDateTime result =
    L*calDateTime.now().plusMinutes(30);*```

---

# 日時の減算

## 日

```java
L*calDate result =
    LocalDate.now*).minusDays(1);
```

## 月

```java*LocalDate result =
    LocalDate.n*w().minusMonths(1);
```

## 年

```*ava
LocalDate result =
    LocalDa*e.now().minusYears(1);
```

## 時間
*```java
LocalDateTime result =
   *LocalDateTime.now().minusHours(1);*```

---

# 日付比較

## より後

```java
*ate1.isAfter(date2);
```

## より前

*``java
date1.isBefore(date2);
```
*## 同じ日付

```java
date1.isEqual(dat*2);
```

---

# 差分計算

## 日数差分

```*ava
long days =
    ChronoUnit.DAY*.between(
        startDate,
     *  endDate
    );
```

## 時間差分

```*ava
long hours =
    ChronoUnit.HO*RS.between(
        startDateTime,*        endDateTime
    );
```

##*分差分

```java
long minutes =
    Ch*onoUnit.MINUTES.between(
        s*artDateTime,
        endDateTime
 *  );
```

## 秒差分

```java
long sec*nds =
    ChronoUnit.SECONDS.betwe*n(
        startDateTime,
        *ndDateTime
    );
```

---

# Dura*ion（時刻差分）

```java
Duration durati*n =
    Duration.between(
        *tartTime,
        endTime
    );

*ong minutes =
    duration.toMinut*s();
```

---

# Period（日付差分）

```*ava
Period period =
    Period.bet*een(
        birthday,
        Loc*lDate.now()
    );

int years = pe*iod.getYears();
int months = perio*.getMonths();
int days = period.ge*Days();
```

---

# 文字列 → 日付

## y*yy-MM-dd

```java
LocalDate date =*    LocalDate.parse("2026-07-02");*```

## yyyy/MM/dd

```java
DateTi*eFormatter formatter =
    DateTim*Formatter.ofPattern(
        "yyyy*MM/dd"
    );

LocalDate date =
  * LocalDate.parse(
        "2026/07*02",
        formatter
    );
```
*## yyyy/MM/dd HH:mm:ss

```java
Da*eTimeFormatter formatter =
    Dat*TimeFormatter.ofPattern(
        "*yyy/MM/dd HH:mm:ss"
    );

LocalD*teTime dateTime =
    LocalDateTim*.parse(
        "2026/07/02 12:30:*0",
        formatter
    );
```

*--

# 日付 → 文字列

## yyyy/MM/dd

```*ava
String result =
    LocalDate.*ow().format(
        DateTimeForma*ter.ofPattern(
            "yyyy/M*/dd"
        )
    );
```

## yyyy*Mdd

```java
String result =
    L*calDate.now().format(
        Date*imeFormatter.ofPattern(
          * "yyyyMMdd"
        )
    );
```

*# yyyy/MM/dd HH:mm:ss

```java
Str*ng result =
    LocalDateTime.now(*.format(
        DateTimeFormatter*ofPattern(
            "yyyy/MM/dd*HH:mm:ss"
        )
    );
```

--*

# よく使うフォーマット一覧

```java
yyyy/MM/*d
yyyy-MM-dd
yyyyMMdd
yyyy/MM/dd H*:mm:ss
yyyy-MM-dd HH:mm:ss
yyyy年MM*dd日
HH:mm:ss
HHmmss
```

---

# 曜日*得

## 英語

```java
DayOfWeek dayOfW*ek =
    LocalDate.now().getDayOfW*ek();
```

出力例

```text
MONDAY
```*
## 日本語

```java
String day =
    *ocalDate.now()
             .getDa*OfWeek()
             .getDisplayN*me(
                 TextStyle.FUL*,
                 Locale.JAPANESE*             );
```

出力例

```text
*曜日
```

---

# 月初・月末取得

## 月初

```*ava
LocalDate firstDay =
    Local*ate.now()
             .withDayOfM*nth(1);
```

## 月末

```java
LocalD*te lastDay =
    LocalDate.now()
 *           .with(
                *TemporalAdjusters
                *    .lastDayOfMonth()
            *);
```

---

# 年初・年末取得

## 年初

```*ava
LocalDate firstDay =
    Local*ate.now()
             .withDayOfY*ar(1);
```

## 年末

```java
LocalDa*e lastDay =
    LocalDate.now()
  *          .with(
                 *emporalAdjusters
                 *   .lastDayOfYear()
             )*
```

---

# タイムゾーン

## JST

```ja*a
ZonedDateTime jst =
    ZonedDat*Time.now(
        ZoneId.of("Asia/*okyo")
    );
```

## UTC

```java*ZonedDateTime utc =
    ZonedDateT*me.now(
        ZoneId.of("UTC")
 *  );
```

---

# LocalDate ⇔ Local*ateTime

## LocalDate → LocalDateT*me

```java
LocalDateTime dateTime*=
    date.atStartOfDay();
```

##*LocalDateTime → LocalDate

```java*LocalDate date =
    dateTime.toLo*alDate();
```

---

# Timestamp変換
*## LocalDateTime → Timestamp

```j*va
Timestamp timestamp =
    Times*amp.valueOf(
        LocalDateTime*now()
    );
```

## Timestamp → L*calDateTime

```java
LocalDateTime*dateTime =
    timestamp.toLocalDa*eTime();
```

---

# 業務で頻出パターン

## 今日の00:00:00

```java
LocalDateTime from =
    LocalDate.now()
             .atStartOfDay();
```

## 今日の23:59:59

```java
LocalDateTime to =
    LocalDate.now()
             .atTime(23, 59, 59);
```

## 直近7日間

```java
LocalDateTime from =
    LocalDate.now()
             .minusDays(7)
             .atStartOfDay();

LocalDateTime to =
    LocalDate.now()
             .atTime(23, 59, 59);
```

## 先月の月初

```java
LocalDate firstDay =
    LocalDate.now()
             .minusMonths(1)
             .withDayOfMonth(1);
```

## 先月の月末

```java
LocalDate lastDay =
    LocalDate.now()
             .withDayOfMonth(1)
             .minusDays(1);
```

## 年齢計算

```java
int age =
    Period.between(
        birthday,
        LocalDate.now()
    ).getYears();
```

## 30日後

```java
LocalDate after30Days =
    LocalDate.now().plusDays(30);
```

## 月末判定

```java
boolean isMonthEnd =
    date.equals(
        date.with(
            TemporalAdjusters
                .lastDayOfMonth()
        )
    );
```

## 土日判定

```java
DayOfWeek day =
    date.getDayOfWeek();

boolean isWeekend =
    day == DayOfWeek.SATURDAY
    || day == DayOfWeek.SUNDAY;
```
