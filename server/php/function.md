$t2 = microtime(true);
echo "t2-t1".'耗时'.round($t2-$t1,3)."秒\n";

array_key_exists 的时间复杂度是 O(1),因为数组内部存储是 hashtable

in_array 效率极低，第三个参数为 true 时表示类型也比较，效率高一丢丢。http://www.zendstudio.net/archives/php-in_array-s-low-performance/#more-1836  性能分析

array_flip + array_key_exists  == in_array 效率大幅度提升。




