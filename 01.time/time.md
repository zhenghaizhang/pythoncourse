# Python的time模块
## time模块的三种时间表示格式
### 时间戳
* 即以整型或浮点型表示的是一个以秒为单位的时间间隔。这个时间的基础值是从1970年的1月1号零点开始算起。
### 时间元组（struct_time）
* 即一种Python的数据结构表示。这个元组有9个整型内容。分别表示不同的时间含义。
  * 索引（Index） 属性（Attribute） 值（Values）
  * 0 tm_year（年） 比如2011
  * 1 tm_mon（月） 1 - 12
  * 2 tm_mday（日） 1 - 31
  * 3 tm_hour（时） 0 - 23
  * 4 tm_min（分） 0 - 59
  * 5 tm_sec（秒） 0 - 61
  * 6 tm_wday（weekday） 0 - 6（0表示周日）
  * 7 tm_yday（一年中的第几天） 1 - 366
  * 8 tm_isdst（是否是夏令时） 默认为-1
    * 夏令时格式，0：表示正常格式，1：表示为夏令时格式，-1：表示根据当前的日期时间格式来判定
    * 名词解释：
      * UTC（Coordinated Universal Time，世界协调时）亦即格林威治天文时间，世界标准时间。在中国为UTC+8。
      * DST（Daylight Saving Time）即夏令时。是一种为节约能源而人为规定地方时间的制度，一般在天亮早的夏季人为将时间提前一小时。
### 格式化的时间字符串
  * 我们常见的标准时间格式，例如2018-03-20 11:25:45等
  * 格式化字符串符号汇总
  * %a 星期几的简写 Weekday name, abbr.
  * %A 星期几的全称 Weekday name, full
  * %b 月分的简写 Month name, abbr.
  * %B 月份的全称 Month name, full
  * %c 标准的日期的时间串 Complete date and time representation
  * %d 十进制表示的每月的第几天 Day of the month
  * %H 24小时制的小时 Hour (24-hour clock)
  * %I 12小时制的小时 Hour (12-hour clock)
  * %j 十进制表示的每年的第几天 Day of the year
  * %m 十进制表示的月份 Month number
  * %M 十时制表示的分钟数 Minute number
  * %S 十进制的秒数 Second number
  * %U 第年的第几周，把星期日做为第一天（值从0到53）Week number (Sunday first weekday)
  *  %w 十进制表示的星期几（值从0到6，星期天为0）weekday number
  *  %W 每年的第几周，把星期一做为第一天（值从0到53） Week number (Monday first weekday)
  *  %x 标准的日期串 Complete date representation (e.g. 13/01/08)
  *  %X 标准的时间串 Complete time representation (e.g. 17:02:10)
  *  %y 不带世纪的十进制年份（值从0到99）Year number within century
  *  %Y 带世纪部分的十制年份 Year number
  *  %z，%Z 时区名称，如果不能得到时区名称则返回空字符。Name of time zone
  *  %% 百分号
## 三种时间表达方式有着不同的用途
  * struct_time便于计算
  * fortmat string便于输出打印，给人查看
  * 而timestamp便于时间数据的存储，节省空间。
####转换方式
  * format_string  --strftime--> struct_time --mktime-->timestamp
  * format_string  <--strptime-- struct_time -localtime/gmtime->timestamp

## time模块中的函数和属性：
* 通过dir(time) 获取出time模块中的函数
  - 'altzone'
  - 'asctime'
  - 'clock'
  - 'ctime'
  - 'daylight'
  - 'get_clock_info'
  - 'gmtime'
  - 'localtime'
  - 'mktime'
  - 'monotonic'
  - 'perf_counter'
  - 'process_time'
  - 'sleep'
  - 'strftime'
  - 'strptime'
  - 'struct_time'
  - 'time'
  - 'timezone'
  - 'tzname'
  - 'tzset'

* altzone – 当地时间与标准UTC时间的差值，单位（秒）
* asctime() – 将时间元组格式转换为字符串形式。可接受一个时间元组，默认为localtime()的返回值
* clock() – 返回当前程序的CPU执行时间。unix系统始终返回全部运行时间；而windows从第二次开始都是以第一次调用此函数时的时间戳作为基准，而不是程序开* 始时间为基准。不接受参数。
* ctime() – 将时间戳转换为字符串。接受一个时间戳，其默认值为当前时间戳。等价于asctime(localtime(seconds)) 结果格式为Tue Mar 20 21:23:35 2018
* daylight – 当地时间是否反映夏令时，默认为0（我们国家不采用夏令时）
* get_clock_info 获取指定时钟的信息。(用的不多)
  - 'clock': time.clock()
  - 'monotonic': time.monotonic() 系统启动，开启的一个时钟，也就是系统开启时间
  - 'perf_counter': time.perf_counter()
  - 'process_time': time.process_time()
  - 'time': time.time()
* gmtime() – 将时间戳转换为UTC时间元组格式。接受一个浮点型时间戳参数，其默认* 值为当前时间戳。
* localtime() – 将时间戳转换为本地时间元组格式。接受一个浮点型时间戳参数，其* 默认值为当前时间戳。
* mktime() – 将本地时间元组转换为时间戳。接受一个时间元组，必选。
* time.monotonic()
* time.perf_counter()
* time.process_time()
* sleep() – 延迟一个时间段，接受整型、浮点型。
* strftime() – 将时间元组以指定的格式转换为字符串形式。接受字符串格式化串、* 时间元组。时间元组为可选，默认为localtime()
* strptime() – 将指定格式的时间字符串解析为时间元组，strftime()的逆向过程* 。接受字符串，时间格式2个参数，都是必选。
* time.struct_time() - 九个参数
* time() – 返回当前时间戳，浮点数形式。不接受参数
* timezone – 当地时间与标准UTC时间的误差，以秒计
* tzname – 关于(标准时区名称, 夏令时时区名称)的元组
* tzset() – 改变本地时区。

三种日期格式的转换方式，及获取方法
时间戳：time.time() # 获取本地时间戳
元组：time.localtime() # 获取本地时间
time.gmtime()  # 获取UTC时间
根据日期字符串获取时间元组time.strptime("2018-03-21", '%Y-%m-%d')
根据日期字符串获取时间元组，再返回人类友好时间time.strftime('%Y-%m-%d',time.strptime("2018-03-21", '%Y-%m-%d'))

获取格式化时间
time.asctime()
time.asctime(res) # res为一个时间元组，可通过time.localtime()获取
time.strftime('%Y-%m-%d %X',time.localtime())

time搞定日期时间变换
