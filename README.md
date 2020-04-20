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
   | จำนวนบิต  | 6 |         26        |
   
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
  ![image](https://onedrive.live.com/?cid=0A6FF7CCC7AFC04A&id=A6FF7CCC7AFC04A%21204&parId=root&o=OneUp)                      
   
 [<br>**homework Clip-1**](https://youtu.be/KGGrDlHpYPE)
 
  ### <br>** อธิบาย homework Clip-2**
        ในคลิป 2 จะพูดถึงการทำงานของ CPU ซึ่งเมื่อเราทำการเปิด switch CPU จะเริ่มอ่านคำสั่งที่บรรทัดแรก แล้วทำการแปลงเป็นเลขฐาน 2 
        หลังจากนั้นก็ทำการดูค่า opcode 6 บิตหน้า ว่าคือคำสั่งอะไร แล้วให้ทำงานอะไร 
* [<br>**homework Clip-2**](https://youtu.be/MUBjTEa2nQo)
  ### Single-Cycle and Multi-Cycle
  ![br](https://s.isanook.com/ns/0/rp/r/w728/ya0xa0m1w0/aHR0cHM6Ly9zLmlzYW5vb2suY29tL25zLzAvdWQvMTYxMC84MDUwMzgyL2NvdmlkLmpwZw==.jpg)
  ### <br>** อธิบาย homework Clip-3**
         ในคลิป 3 จะพูดถึงความแตกต่างระหว่าง single-cycle และ multi-cycle
* [<br>**homework Clip-3**](https://youtu.be/-e2fQUB4PIY)
 
* [<br>**homework Clip-4**](https://youtu.be/lUhIu3NA02Y)
  * อธิบายคำสั่ง lw ในcyclc
* [<br>**homework Clip-5**](https://youtu.be/731dgwT8FfE)
  * อธิบายคำสั่ง beq ในcyclc
* [<br>**homework Clip-6**](https://youtu.be/WjuaH1VdVnQ)
  * อธิบายคำสั่ง R-type
