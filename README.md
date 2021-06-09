# captcha
tp验证码独立版


## 安装
composer require ilbsfx/captcha

## 配置参数（可选）
| 参数 | 描述 | 默认
---- | ---- | ----
| codeSet | 验证码字符集合 | 略
| expire  | 验证码过期时间（s）  | 1800
| math    | 使用算术验证码 | false
| useZh   | 使用中文验证码 | false
| zhSet   | 中文验证码字符串    | 略
| useImgBg    | 使用背景图片  | false
| fontSize    | 验证码字体大小(px) | 25
| useCurve    | 是否画混淆曲线 | true
| useNoise    | 是否添加杂点  | true
| imageH  | 验证码图片高度，设置为0为自动计算   | 0
| imageW  | 验证码图片宽度，设置为0为自动计算   | 0
| length  | 验证码位数   | 5
| fontttf | 验证码字体，不设置是随机获取  | 空
| bg  | 背景颜色    | [243, 251, 254]
| reset   | 验证成功后是否重置   | true

## 使用
```php
use Colton\Captcha\CaptchaBuilder;

//（可选参数）
$config = [
    //验证码位数
    'length'   => 5,
    // 验证码字符集合
    'codeSet'  => '2345678abcdefhijkmnpqrstuvwxyzABCDEFGHJKLMNPQRTUVWXY',
    // 验证码过期时间
    'expire'   => 1800,
    // 是否使用中文验证码
    'useZh'    => false,
    // 是否使用算术验证码
    'math'     => true,
    // 是否使用背景图
    'useImgBg' => false,
    //验证码字符大小
    'fontSize' => 25,
    // 是否使用混淆曲线
    'useCurve' => true,
    //是否添加杂点
    'useNoise' => true,
    // 验证码字体 不设置则随机
    'fontttf'  => '',
    //背景颜色
    'bg'       => [243, 251, 254],
    // 验证码图片高度
    'imageH'   => 0,
    // 验证码图片宽度
    'imageW'   => 0
];

$captcha = new CaptchaBuilder($config);

// 获取验证码key
$_SESSION['key'] = $captcha->getCodeKey();

// 输出验证码图片
$captcha->output();


// 验证验证码是否正确
$userInput = $_POST['code'];
$res = $captcha->check($userInput, $_SESSION['key']);
if ($res === true) {
    // 验证码正确
} else {
    // 验证码错误
}
```
