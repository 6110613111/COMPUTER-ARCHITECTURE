# รางานวิชา สถาปัตยกรรมคอมพิวเตอร์ [CN210]
## <br>**MIPS Instruction format**
   - ทุกคำสั่งมีขนาด 32 บิต
   - มีทั้งหมด 3 คำสั่ง ได้แก่ R-Format(คำสั่งใช้ในการคำนวณ),I-Format(คำสั่งย้ายข้อมูล)และJ-Format(คำสั่งกระโดดไปทำงานที่อื่น)
   
### <br>**R - Format**

  | โครงสร้าง | op | rs | rt | rd | shamt | func |      
  |----------|----|----|----|----|-------|------| 
  | จำนวนบิต  | 6  |  5 |  5 |  5 |   5   |   6  | 
            
            * ALU            func$rd,$rs,$st  
            
### <br>**I - Format**

   | โครงสร้าง | op | rs | rt | value or offset |         
   |----------|----|----|----|-----------------|        
   | จำนวนบิต  |  6 | 5  |  5 |      16         |
            * ALUi           alui $rt,$rs,value                                
            * Data Tranfer   lw $rt,offset($rs) 
                             sw $rt,offset($rs) 
            * Branch         beq $rs,$tr,offset 
            
### <br>**J - format**

   | โครงสร้าง | op | absolute address |
   |----------|----|------------------|
   | จำนวนบิต  | 6  |         26       |
   
            * Jump           j address
            
### ALU decoder
   | Machine opcode | Instruct Format| Opcode | Function |
   |----------------|----------------|--------|----------|
   |        lw      |       I-type   | 100011 |  xxxxxx  |
   |        sw      |       I-type   | 101011 |  xxxxxx  |
   |       beq      |       I-type   | 000100 |  xxxxxx  |
   |       add      |       R-type   | 000000 |  100000  |
   |       and      |       R-type   | 000000 |  100010  |
   |        or      |       R-type   | 000000 |  100101  |
   |       slt      |       R-type   | 000000 |  101010  |
    
### <br>**อธิบาย homework Clip-1** 
   
         ในคลิป 1 จะพูดถึงคำสั่ง Jump เป็นคำสั่งที่ให้กระโดดไปทำงานที่ตำปหน่งอื่น เมื่อทำเสร็จแล้วให้กระโดดมาทำงานที่ตำแหน่งเดิมต่อ
         คำสั่ง Jump มีทั้งหมด 32 บิต ประกอบด้วย opcode 6 บิต และ address 26 บิต
         1.ทำการหาค่า address โดยการนำค่า fib_exit มาแปลงเป็นเลขฐาน 2 แล้ว >>2 หลังจากนั้นตัด 4 บิตหน้าอออก
         2.จะได้ค่า address 26 บิต แล้วเอาไปรวมกับค่า opcode ของ Jump                   
   
[<br>**homework Clip-1**](https://youtu.be/KGGrDlHpYPE)
 
### <br>**อธิบาย homework Clip-2**
 
        ในคลิป 2 จะพูดถึงการทำงานของ CPU ซึ่งเมื่อเราทำการเปิด switch CPU จะเริ่มอ่านคำสั่งที่บรรทัดแรก แล้วทำการแปลงเป็นเลขฐาน 2 
        หลังจากนั้นก็ทำการดูค่า opcode 6 บิตหน้า ว่าคือคำสั่งอะไร แล้วให้ทำงานอะไร 
        
[<br>**homework Clip-2**](https://youtu.be/MUBjTEa2nQo)
 
### Von Neuman and Harvard Architrctures
![br](https://vivadifferences.com/wp-content/uploads/2019/10/Von-Neuman-Vs-Harvard-Architecture.png)

      * Von Neuman 
         - มี memory 1 ชุด รวม instruction and data เข้าด้วยกัน ดังนั้นเครื่องจะมีขนาดใหญ่
      * Harvard Architrctures
         - มี memory 2 ชุด คือแยก instruction and data ออกจากกัน
         
### Single-Cycle 
  ![br](https://cseweb.ucsd.edu/~j2lau/cs141/single_cycle_cpu_datapath.png)
  
### Multi-Cycle
  ![br](https://cseweb.ucsd.edu/~j2lau/cs141/multi_cycle_cpu_datapath.png)
  
    Single-Cycle                                              Multi-Cycle
     - ไม่มีประสิทธิภาพเท่าแบบ Multi-Cycle                           - มีประสิทธิภาพมากกว่าแบบ Single-Cycle
     - memory 2 ชุด แยกออกจากกัน เป็นแบบ Harvard Architecture      - มี memory 1 ชุด เป็นแบบ Von Neuman Architecture
     - มี ALU มากกว่า 1 ตัวในการรองรับinputทั้งหมดในการทำงาน 1 รอบ    - มี ALU 1 ตัวในการรองรับinputทั้งหมดในการทำงาน 1 รอบ     
     
### <br>**อธิบาย homework Clip-3**
  
         ในคลิป 3 จะพูดถึงความแตกต่างระหว่าง single-cycle และ multi-cycle
         
[<br>**homework Clip-3**](https://youtu.be/-e2fQUB4PIY)
 
### <br>**อธิบาย homework Clip-4**
 
         ในคลิป 4 จะพูดถึงคำสั่ง lw in cycle ซึ่งมีทั้งหมด 5 step(T1-T5)
         T1 เมื่อทำการเปิด switch PC จะทำการอ่านคำสั่งในmemory แล้วนำข้อมูลที่อ่านไปเก็บไว้ใน instruction register
            ในขณะเดียวกัน PC จะนำ PCไปบวก4 ที่ ALU แล้วทำการเอา PC+4 มาเก็บไว้แทนที่ PCเดิม
         T2 นำค่าที่เก็บอยู่ใน instruction register มาเก็บไว้ที่ A และB (register1(rs) and register2(rt))
            ขณะเดียวกันนั้น ก็นำค่าoffset มาSign extend จาก 16 > 32 บิต แล้วนำมาเก็บไว้ที่ ALU
         T3 นำค่า register1 ไปบวกกับ ค่าoffset ที่ALU แล้วนำค่าไปเก็บที่ ALUOut
         T4 ส่งค่าที่เก็บใน ALUOut ไปให้memory แล้วmemory จะส่งค่านี้ไปเก็บไที่ memory data register
         T5 ส่งค่าที่เก็บในmemory data register ไปให้ register2
         
[<br>**homework Clip-4**](https://youtu.be/lUhIu3NA02Y)
  
### <br>**อธิบาย homework Clip-5**
  
         ในคลิป 5 จะพูดถึงคำสั่ง beq in cycle ซึ่งมีทั้งหมด 3 step(T1-T3)
         T1 เมื่อทำการเปิด switch PC จะทำการอ่านคำสั่งในmemory แล้วนำข้อมูลที่อ่านไปเก็บไว้ใน instruction register
         T2 นำค่าที่เก็บอยู่ใน instruction register มาเก็บไว้ที่ A และB (register1(rs) and register2(rt))
            ขณะเดียวกันนั้น ก็นำค่าoffset มาSign extend จาก 16 > 32 บิต แล้วนำมาเก็บไว้ที่ ALU
         T3 นำค่า register1 กับ register2 มาลบกันที่ALU แล้วถ้าเป็นูนย์ คำสั่งก็จะไปทำงานที่ addressนั้น (address ก็คือค่า offset)
         
[<br>**homework Clip-5**](https://youtu.be/731dgwT8FfE)
 
### <br>**อธิบายhomework Clip-6**
  
         ในคลิป 6 จะพูดถึงคำสั่ง R-type ซึ่งมีทั้งหมด 4 cycle(T1-T4)
         T1 เมื่อทำการเปิด switch PC จะทำการอ่านคำสั่งในmemory แล้วนำข้อมูลที่อ่านไปเก็บไว้ใน instruction register
            ในขณะเดียวกัน PC จะนำ PCไปบวก4 ที่ ALU แล้วทำการเอา PC+4 มาเก็บไว้แทนที่ PCเดิม
         T2 นำค่าที่เก็บอยู่ใน instruction register มาเก็บไว้ที่ A และB (register1(rs) and register2(rt))
            * ไม่มีค่า offset เพราะว่าเราทำคำสั่ง R-type
         T3 นำค่า register1 กับ register2 มาคำนวณกันที่ALU แล้วเอาผลลัพธ์ที่ได้มาเก็บใน ALUOut
         T4 นำค่า ALUOut ไปเก็บไว้ใน register2
         
[<br>**homework Clip-6**](https://youtu.be/WjuaH1VdVnQ)
  
