1.下载log4php,文件夹命名为log4php,放到appliaction-third_party下
http://logging.apache.org/log4php/download.html

2.log4php.properties文件也放到log4php下

    log4php.rootLogger=DEBUG, A2  
      
    #\u8f93\u51fa\u5230\u9875\u9762
    log4php.appender.A1 = LoggerAppenderEcho  
    log4php.appender.A1.layout = LoggerLayoutHtml  
      
    #\u8f93\u51fa\u5230\u6587\u4ef6
    log4php.appender.A2 = LoggerAppenderDailyFile  
    log4php.appender.A2.layout = LoggerLayoutPattern  
    log4php.appender.A2.layout.ConversionPattern = "%d{ISO8601} [%p] %c: %m (at %F line %L)%n"  
    log4php.appender.A2.datePattern = Y-m-d  
    log4php.appender.A2.file = ../logs/%s.log  
    
3.在控制器中定义个成员变量$mLog,在构造器中实例化Logger
class MY_Controller extends MX_Controller {
    protected $mLog;
    public function __construct()
    {
        $this->mLog = Logger::getLogger(__CLASS__);
    }

}

class Login extends MY_Controller {
    public function __construct()
    {
        parent::__construct();
    }
    $this->mLog->info('这是info日志');
}
