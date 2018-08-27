编码

https://developer.mozilla.org/zh-CN/docs/Web/API/WindowBase64/btoa

function utf8_to_b64( str ) {
    return window.btoa(unescape(encodeURIComponent( str )));
}

function b64_to_utf8( str ) {
    return decodeURIComponent(escape(window.atob( str )));
}


http://levy.work/2017-03-24-black-magic-js-atob-with-utf8/

原理是escape对编码有转换，从latin转到ucs，所以能实现utf8到ucs的转换

escape只对基本平面的有处理，扩展平面是不支持的。
但是怎么样支持unicode扩展平面，还需要查询

http://outofmemory.cn/code-snippet/1179/php-achieve-javascript-de-escape-unescape-function

http://ecmanaut.blogspot.com/2006/07/encoding-decoding-utf8-in-javascript.html
