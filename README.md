# รางานวิชา สถาปัตยกรรมคอมพิวเตอร์ [CN210]
## <br>**MIPS Instruction format**
   - ทุกคำสั่งมีขนาด 32 บิต
   - มีทั้งหมด 3 คำสั่ง ได้แก่ R-Format(คำสั่งใช้ในการคำนวณ), I-Format(คำสั่งย้ายข้อมูล) และJ-Format(คำสั่งกระโดดไปทำงานที่อื่น)
   
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
![br](https://github.com/6110613319/COMPUTER-ARCHITECTURE/blob/master/jumpping.JPG?raw=true)                  
[<br>**homework Clip-1**](https://youtu.be/KGGrDlHpYPE)
 
### <br>**อธิบาย homework Clip-2**
![br](https://github.com/6110613319/COMPUTER-ARCHITECTURE/blob/master/pic2.png?raw=true)       
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
  
### <br>**อธิบาย homework Clip-3**
![br](https://github.com/6110613319/COMPUTER-ARCHITECTURE/blob/master/pic3.png?raw=true)         
[<br>**homework Clip-3**](https://youtu.be/-e2fQUB4PIY)
 
### <br>**อธิบาย homework Clip-4**
![br](https://github.com/6110613319/COMPUTER-ARCHITECTURE/blob/master/pic4.png?raw=true)        
[<br>**homework Clip-4**](https://youtu.be/lUhIu3NA02Y)
  
### <br>**อธิบาย homework Clip-5**
![br](https://github.com/6110613319/COMPUTER-ARCHITECTURE/blob/master/pic5.png?raw=true)         
[<br>**homework Clip-5**](https://youtu.be/731dgwT8FfE)
 
### <br>**อธิบายhomework Clip-6**
![br](https://github.com/6110613319/COMPUTER-ARCHITECTURE/blob/master/pic6.png?raw=true)
[<br>**homework Clip-6**](https://youtu.be/WjuaH1VdVnQ)

## <br>**Pipelining**
![br](https://github.com/6110613319/COMPUTER-ARCHITECTURE/blob/master/comp-arch-2012-choompol-110.JPG?raw=true)

         - Single Cycle : ทุกคำสั่งทำงานจบพร้อมกันภายใน 1 cycle ดังนั้นจึงใช้เวลามากที่สุด
         - Multiple Cycle : ทำงานหลายcycle
         - Pipeline : ทำงานหลายcycle โดยคำสั่งเเรกยังทำงานไม่จบ คำสั่งต่อไปสามารถทำงานได้เลย ดังนั้นจึงใช้เวลาน้อยที่สุด
 
 ![br](https://github.com/6110613319/COMPUTER-ARCHITECTURE/blob/master/pic7.png?raw=true)
 
         จากรูปจะเห็นว่า - เมื่อถุงA ทำการอบอยู่ ถุงB ก็เริ่มทำการซักผ้า 
                      - เมื่อถุงA ทำการพับผ้า ถุงB ก็เริ่มทำการอบผ้า ถุงC ก้เริ่มทำการซักผ้า
                      - เมื่อถุงA เสร็จสิ้นการทำงาน ถุงB ก็เริ่มทำการพับผ้า ถุงC ก็เริ่มทำการอบผ้า
                      - เมื่อถุงB เสร็จสิ้น ถุงC ก้เริ่มทำการพับผ้า
                      - ถุงC เสร็จสิ้น
                      * ขอไม่อธิบายถุงD
         จากคำอธิบายการทำงานของการซักผ้า จะเห็นว่าเมื่อคำสั่งที่ 1 ยังไม่เสร็จสิ้นก้เริ่มทำคำสั่งต่อไปทันที 
         ซึ่งการทำงานแบบนี้(Pipeline)เป็นการประหยัดเวลาในการทำงาน

### <br>**อธิบายhomework Clip-7**
![br](https://github.com/6110613319/COMPUTER-ARCHITECTURE/blob/master/Screen%20Shot%202563-04-28%20at%2015.00.36.png?raw=true) 
[<br>**homework Clip-7**](https://youtu.be/0FaH8bjTsxM)
