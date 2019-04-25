# laravel-docker
สร้าง laravel โปรเจค
```
laravel new my-project
```

clone laradock มาไว้ใน directory ของโปรเจค
```
git clone https://github.com/Laradock/laradock.git 
```

เข้าไปยัง directory ที่ชื่อว่า laradock จากนั้น ทำการคัดลอก env-example แล้วเปลี่ยนชื่อเป็น .env
```
cd laradock
cp env-example .env
```

ตั้งค่า .env จากค่าเริ่มต้นของ laradock
```
DB_CONNECTION=mysql
DB_HOST=mariadb #IP ของ host ถ้าเราใช้ mysql container ก็ใส่ mysql แทน
DB_PORT=3306
DB_DATABASE=defaul
DB_USERNAME=root
DB_PASSWORD=root
```

สร้าง container จากไฟล์ docker-compose.yml
```
docker-compose up -d nginx mariadb workspace
```

ssh ไปยัง docker container ที่ชื่อว่า workspace
```
docker-compose exec --user laradock workspace bash
```

ติดตั้งแพคเกจต่างของ Laravel ด้วยคำสั่ง
```
composer install
php artisan key:generate
php artisan migrate
```

หากเราต้องการเชคสถานะสามารถทำได้โดย
```
docker ps
```

Referral
* [laradock.io](https://laradock.io/)
* [สร้าง-laravel-environments-บน-docker-ง่ายๆด้วย-laradock-7c5abf362538](https://medium.com/@anuchamaitripirom/สร้าง-laravel-environments-บน-docker-ง่ายๆด้วย-laradock-7c5abf362538)
