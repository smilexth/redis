# Redis Stack

## รายละเอียด
Redis Stack คือชุดคอนเทนเนอร์ที่ประกอบด้วย Redis Server และ RedisInsight ซึ่งเป็นเครื่องมือสำหรับจัดการและมอนิเตอร์ Redis

## ข้อกำหนดเบื้องต้น
- Docker และ Docker Compose
- ไฟล์ `.env` ที่มีตัวแปรต่อไปนี้:
  - `REDIS_PASSWORD`: รหัสผ่านสำหรับ Redis
  - `TIMEZONE`: โซนเวลาของคุณ (เช่น Asia/Bangkok)

## การตั้งค่า
1. สร้างไฟล์ `.env` ในโฟลเดอร์นี้ (ถ้ายังไม่มี) และกำหนดค่าตัวแปรที่จำเป็น:
   ```
   REDIS_PASSWORD=รหัสผ่านที่ปลอดภัย
   TIMEZONE=Asia/Bangkok
   ```

2. ปรับแต่งไฟล์ `docker-compose.yml` ตามความต้องการ

## การเริ่มใช้งาน
เริ่มต้นบริการด้วยคำสั่ง:
```bash
docker-compose up -d
```

## การเข้าถึง
- **Redis Server**: เข้าถึงได้ที่ `localhost:6379`
- **RedisInsight**: เข้าถึงได้ที่ `http://localhost:5540` ผ่านเว็บเบราว์เซอร์

### การเชื่อมต่อกับ RedisInsight
1. เปิดเบราว์เซอร์และไปที่ `http://localhost:5540`
2. ในการตั้งค่าการเชื่อมต่อใหม่ ใช้ค่าต่อไปนี้:
   - Host: redis
   - Port: 6379
   - Name: ตั้งชื่อการเชื่อมต่อตามที่ต้องการ
   - Username: default (หรือเว้นว่างไว้)
   - Password: รหัสผ่านที่คุณกำหนดใน REDIS_PASSWORD

## การใช้งานพื้นฐาน
- Redis นี้ถูกกำหนดค่าให้ต้องใช้รหัสผ่านสำหรับการเชื่อมต่อทั้งหมด
- ข้อมูลจะถูกเก็บไว้ในโวลุ่ม Docker ที่ชื่อ `redis_data`
- การตั้งค่า RedisInsight จะถูกเก็บไว้ในโวลุ่ม Docker ที่ชื่อ `redisinsight_data`
- บริการทั้งหมดเชื่อมต่อกันผ่านเครือข่าย `ai-network`

## การหยุดบริการ
หยุดบริการด้วยคำสั่ง:
```bash
docker-compose down
```

ถ้าต้องการลบโวลุ่มข้อมูลด้วย:
```bash
docker-compose down -v
```
