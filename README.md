# -
总结遇到的大坑（小项目出问题病急乱投医使不得）


uwsgi+nginx部署django时，出现502badgate错误，查错误日志一直是下面语句，把百度的100个方法试完也解决不了，其实是你的代码有错误，
不信在命令行python manage.py runserver 8001一下就明白了
upstream prematurely closed connection while reading response header from upstream, client


调微信接口时总是提示errorcode4001，access_token失效或过期，其实把access_token先存到数据库，用时再拿出来就好了
10_RrSmG0SAuyhfeTrD1OqMPUPjcpcv0U-KcXjwRVpY7hHRH20pyixKWD3XVC6vs_gLxxin84k7pTOjlsLuj9Q0bQ

凡是服务器报500或502错误一定是代码哪里有错误，跟服务器基本没关系

解决nginx问题
sudo CC=gcc pip install uwsgi

常用命令
启动服务器
uwsgi --ini face_to_face.ini
/etc/init.d/nginx restart

停止使用
sudo killall -9 uwsgi
service nginx stop

nginx配置文件目录
sudo vim /etc/nginx/nginx.conf

nginx原始配置
2
65
2048

日志
sudo vim face_to_face.ini
vim /var/log/nginx/face_to_face_error.log
vim /var/log/nginx/face_to_face_access.log

试运行uwsgi
uwsgi --http 122.152.219.23:80 --file face_to_face/wsgi.py --static-map=/static=static



解决pip不能用的问题
python -m ensurepip
easy_install pip

# 若有权限错误，则在命令前面添加sudo
sudo easy_install pip

linux命令
mv before.txt after.txt 
cp -r dir1 dir2


