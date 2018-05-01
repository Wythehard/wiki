```
根据权重进行排序。
uasort($items, function($a, $b) {
 $aw = (int) isset($a['weight']) ? $a['weight'] : 0;
 $bw = (int) isset($b['weight']) ? $b['weight'] : 0;
 if ($aw == $bw) {
  return 0;
 }
 return ($a < $b) ? -1 : 1;
});
```