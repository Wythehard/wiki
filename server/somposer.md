配置镜像源

>  composer config -g repo.packagist composer https://packagist.phpcomposer.com


如果还安装了其他镜像源，可以通过编辑全局 composer 配置变量来手动删除和更改

>composer config --editor --global
>
>列出配置
>
>composer config --list



docker 中的 composer，需要先 docker pull composer
```
通过 docker 容器来执行composer 命令  其中 `--ignore-platform-reqs --no-scripts` 忽略一些 PHP 的依赖 直接安装依赖包。

docker run --rm --interactive --tty \
    --volume $PWD:/app \
    --volume $PWD/../composer-config:/tmp \
    composer install --ignore-platform-reqs --no-scripts
```

