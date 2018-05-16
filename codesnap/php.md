##### 标准输入
```
<?php   
while (fscanf(STDIN, "%d%d", $a, $b) == 2) {  
    printf("%d\n",$a+$b);
} 求ab和



<?php
while(fscanf(STDIN, "%d", $n) == 1)  {
    $ans=0;
    for($i=0;$i<$n;$i++){
        //read whole line
        fscanf(STDIN, "%[^\n]s", $line);
        //split line to array
        $numbers = explode(" ", trim($line));
        foreach ($numbers as $number){
            $ans = $ans + intval($number);
        }
    }
    printf("%d\n", $ans);
}

```