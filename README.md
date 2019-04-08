# Merge-Sort-in-Assemb
data segment
array  db 9,6,5,4,3,2,1,8   
count  dw 8
ends

stack segment
    dw   128  dup(0)
ends

code segment
    mov ax,@data
    mov ds,ax
    mov cx,count      
    dec cx 
                 
nextscan:                
    mov bx,cx
    mov si,0 

nextcomp:
      
    mov al,array[si]
    mov dl,array[si+1]
    cmp dl,al  

    jnc burasi  
    
    mov array[si],al
    
    jmp noswap 
    
burasi: 

    mov array[si],dl 
    
noswap:  
    
    inc si 
    inc si
    dec bx  
    dec bx 
    cmp bx,1
    jz nextcomp

    loop nextscan       ; } while(--cx);
     
    
 ;; now we are comparing [0],[2],[4],[6] values. 
   
    mov cx,4      
    dec cx 
                 

nextscan2:                
    mov bx,cx
    mov si,0 

nextcomp2:
      

    mov al,array[si]
    mov dl,array[si+2]
    cmp dl,al  

    jnc burasi2  
    
    mov array[si],al
    
    jmp noswap2 
    
burasi2: 

    mov array[si],dl 


noswap2:  
    
    inc si 
    inc si
    dec bx
    dec bx
    cmp bx,1
    jz nextcomp

    loop nextscan2
              
    
    mov cx,2      
    dec cx 
                  
      
nextscan3:                
    mov bx,cx
    mov si,0 

nextcomp3:
      

    mov al,array[si]
    mov dl,array[si+2]
    cmp dl,al  

    jnc burasi3  
    
    mov array[si],al
    
    jmp noswap3 
      
burasi3: 

    mov array[si],dl 


noswap3:  
    
    inc si 
    inc si
    dec bx 
    dec bx  
    cmp bx,1
    jz nextcomp3

    loop nextscan3                

mov ax, 4c00h
int 21h  


ends
