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
   ### ALU Codeer
   | Machine opcode | Instruct Format| Opcode | Function |
   |----------------|----------------|--------|----------|
   |        lw      |       I-type   | 100011 |  xxxxxx  |
   |        sw      |       I-type   | 101011 |  xxxxxx  |
   |       beq      |       I-type   | 000100 |  xxxxxx  |
   |       add      |       R-type   | 000000 |  100000  |
   |       and      |       R-type   | 000000 |  100010  |
   |        or      |       R-type   | 000000 |  100101  |
   |       slt      |       R-type   | 000000 |  101010  |
   
   ### <br>**Assembling JUMP Instructions**  
       
                                         
   
    


* [<br>**homework Clip 1**](https://youtu.be/KGGrDlHpYPE)
  * อธิบายคำสั่ง JUMP 
* [<br>**Clip 2**](https://youtu.be/MUBjTEa2nQo)
  * อธิบายหลักการทำงานของ CPU 
* [<br>**Clip 3**](https://youtu.be/-e2fQUB4PIY)
  * อธิบายความต่างระหว่าง single-cycle and multy-cycle
* [<br>**Clip 4**](https://youtu.be/lUhIu3NA02Y)
  * อธิบายคำสั่ง lw ในcyclc
* [<br>**Clip 5**](https://youtu.be/731dgwT8FfE)
  * อธิบายคำสั่ง beq ในcyclc
* [<br>**Clip 6**](https://youtu.be/WjuaH1VdVnQ)
  * อธิบายคำสั่ง R-type
