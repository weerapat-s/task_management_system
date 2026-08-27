# Task Management System

ระบบจัดการงาน (Task Management System) สำหรับปฏิบัติการ Session 07
หัวข้อ: Git, OOP, SOLID, Component-Based Design, Refactoring, Clean Code, Code Review และ CI/CD

## โครงสร้างไฟล์

| ไฟล์ | คำอธิบาย |
|------|----------|
| `procedural_tasks.py` | เวอร์ชันแรก เขียนแบบ Procedural ใช้ global list เก็บ task |
| `oop_tasks.py` | Refactor เป็น OOP แยกเป็น `Task` และ `TaskManager` |
| `srp_tasks.py` | ใช้ SOLID (SRP + OCP) แยก `TaskStorage` ออกจาก `TaskManager` ด้วย Dependency Injection |
| `.github/workflows/main.yml` | GitHub Actions CI/CD pipeline (lint + test) |

## วิธีรัน

```bash
python procedural_tasks.py
python oop_tasks.py
python srp_tasks.py
```

## สรุปแนวคิด

1. **Procedural → OOP**: ย้ายจาก global data มาเป็น attribute ของ object ลดปัญหาข้อมูลถูกแก้จากทุกที่
2. **SRP**: `TaskManager` ดูแล business logic อย่างเดียว, `FileTaskStorage` ดูแล persistence
3. **OCP**: เพิ่ม storage แบบใหม่ (เช่น `DatabaseTaskStorage`) ได้โดยไม่แก้ `TaskManager`
4. **Code Review**: ทำงานผ่าน feature branch → Pull Request → review → merge
5. **CI/CD**: ทุก push/PR เข้า `main` จะรัน lint และ test อัตโนมัติ
