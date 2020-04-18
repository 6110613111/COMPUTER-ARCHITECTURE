# รางานวิชา สถาปัตยกรรมคอมพิวเตอร์ [CN210]
## <br>**MIPS Instruction format**
   - ทุกคำสั่งมีขนาด 32 บิต
   ### <br>**R - Format**
  | โครงสร้าง | op | rs | rt | rd | shamt | func |      
  |----------|----|----|----|----|-------|------| 
  | จำนวนบิต  | 6  |  5 |  5 |  5 |   5   |   6  | 
            
            * ALU            func$rd,$rs,$st                
               
               
   ### <br>**I - Format**
   | op | rs | rt | value or offset |         
   |----|----|----|-----------------|        
   
            * ALUi           alui $rt,$rs,value                                
            * Data Tranfer   lw $rt,offset($rs) 
                             sw $rt,offset($rs) 
            * Branch         beq $rs,$tr,offset 
   ### <br>**J - format**
   | op | absolute address |
   |----|------------------|
   
            * Jump           j address
   ### <br>**Assembling JUMP Instructions**  
       
                                         
   
    


* [<br>**Clip 1**](https://youtu.be/KGGrDlHpYPE)
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
