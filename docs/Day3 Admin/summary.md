# สรุป ความเข้าใจ

# OpenStack Dalmatian (2024.2) Services and Their Roles

OpenStack เป็นแพลตฟอร์มโอเพ่นซอร์สสำหรับ Cloud Infrastructure-as-a-Service (IaaS) มีบริการหลากหลายที่ช่วยจัดการทรัพยากรในดาต้าเซ็นเตอร์:

## บริการหลักใน OpenStack Dalmatian

1. **Nova** (Compute Service)

   - จัดการและสร้าง Virtual Machines (VMs)
   - รองรับ GPU สำหรับงาน AI และ Machine Learning

2. **Neutron** (Networking Service)

   - จัดการเครือข่าย Virtual Network เช่น Load Balancers, Firewalls

3. **Cinder** (Block Storage Service)

   - จัดการ Volume Storage สำหรับ Virtual Machines และแอปพลิเคชัน

4. **Glance** (Image Service)

   - เก็บและจัดการ VM Images เช่น Image สำหรับสร้าง Virtual Machine

5. **Swift** (Object Storage Service)

   - จัดเก็บข้อมูลแบบ Object Storage เหมาะสำหรับไฟล์ขนาดใหญ่หรือข้อมูลที่ไม่ต้องการ Block Storage

6. **Horizon** (Dashboard)

   - แดชบอร์ดแบบ Web UI สำหรับผู้ใช้งานและผู้ดูแลระบบในการจัดการทรัพยากร

7. **Keystone** (Identity Service)

   - จัดการการยืนยันตัวตนและสิทธิ์การเข้าถึงบริการต่าง ๆ ใน OpenStack

8. **Heat** (Orchestration Service)

   - ช่วยจัดการ Deployment Automation ของทรัพยากร เช่น การตั้งค่า VM และเครือข่ายแบบอัตโนมัติ

9. **Ironic** (Bare Metal Provisioning Service)

   - สำหรับการจัดการ Bare Metal Server รองรับการใช้งานกับ Infrastructure-as-a-Service

10. **Manila** (Shared File System Service)

- จัดการและแชร์ไฟล์ผ่าน Network File System (NFS) และ CIFS

## ฟีเจอร์ใหม่ใน OpenStack Dalmatian

- **Skyline UI**: ส่วนติดต่อผู้ใช้แบบใหม่ที่ใช้งานง่ายและทันสมัย
- รองรับ Workload ที่หลากหลาย เช่น AI, HPC และ Machine Learning

![](../assets/images/skyline_ui.jpg)

## Watch Skyline UI introduction

![](../assets/images/skyline_ui2.jpg)

[https://www.youtube.com/watch?v=pFAJLwzxv0A](https://www.youtube.com/watch?v=pFAJLwzxv0A)

### อ้างอิง

- [OpenStack Documentation](https://docs.openstack.org)
- [OpenStack Dalmatian Release Notes](https://releases.openstack.org)
