# Tema3

                                                             hola                                                                            
//Cuevas Martinez Adrian de Jesus 19211623
@ greet.s - a little asm greeter.
@ programa corto que obtiene la entrada del teclado y luego lo imprime de nuevo en la pantalla.


.section        .bss
.comm buffer, 48             @ reserve 48 byte buffer

.section        .data
msg:
        .ascii  "** Greeter **\nPlease enter your name: "
msgLen = . - msg
msg2:
        .ascii  "Hello "
msg2Len = . - msg2

.section        .text
.globl  _start
_start:

mov r0, $1                  @ print program's opening message   
ldr r1, =msg
ldr r2, =msgLen
mov r7, $4
svc $0

mov r7, $3                  @ read syscall
mov r0, $1
ldr r1, =buffer
mov r2, $0x30
svc $0

mov r0, $1                  @ print msg2
ldr r1, =msg2
ldr r2, =msg2Len
mov r7, $4
svc $0

mov r0, $1                  @ now print the user input
ldr r1, =buffer
mov r2, $0x30
mov r7, $4
svc $0

mov r7, $1                  @ exit syscall
mov r7, $4
svc $0

mov r7, $3                  @ read syscall
mov r0, $1
ldr r1, =buffer
mov r2, $0x30
svc $0

mov r0, $1                  @ print msg2
ldr r1, =msg2
ldr r2, =msg2Len
mov r7, $4
svc $0

mov r0, $1                  @ now print the user input
ldr r1, =buffer
mov r2, $0x30
mov r7, $4
svc $0

mov r7, $1                  @ exit syscall
svc $0                      @ wake kernel
.end



Ejercicio2
//Cuevas Martinez Adrian de Jesus 19211623
.data
var1 : .byte 0b00110010
.align
var2 : .byte 0b11000000
.align
.text
.global main
main : ldr r1, = var1 /* r1 <- & var1 */
ldrsb r1, [ r1 ] /* r1 <- *r1 */
ldr r2, = var2 /* r2 <- & var2 */
ldrsb r2, [ r2 ] /* r2 <- *r2 */
add r0, r1, r2 /* r0 <- r1 + r2 */
bx lr



Ejercicio2.1
//Cuevas Martinez Adrian de Jesus 19211623
 .arch armv6
        .eabi_attribute 28, 1
        .eabi_attribute 20, 1
        .eabi_attribute 21, 1
        .eabi_attribute 23, 3
        .eabi_attribute 24, 1
        .eabi_attribute 25, 1
        .eabi_attribute 26, 2
        .eabi_attribute 30, 6
        .eabi_attribute 34, 1
        .eabi_attribute 18, 4
        .file   "Ejercicio2.1.c"
        .text
        .section        .rodata
        .align  2
        .type   _ZStL19piecewise_construct, %object
        .size   _ZStL19piecewise_construct, 1
        _ZStL19piecewise_construct:
        .space  1
        .local  _ZStL8__ioinit
        .comm   _ZStL8__ioinit,1,4
        .align  2
.LC0:
        .ascii  "\012\000"
        .text
        .align  2
        .global main
        .arch armv6
        .syntax unified
        .arm
        .fpu vfp
        .type   main, %function
main:
        .fnstart
.LFB1512:
        @ args = 0, pretend = 0, frame = 8
        @ frame_needed = 1, uses_anonymous_args = 0
        push    {fp, lr}
        .save {fp, lr}
        .setfp fp, sp, #4
        add     fp, sp, #4
        .pad #8
        sub     sp, sp, #8
        mov     r3, #100
         str     r3, [fp, #-8]
        mov     r3, #0
        str     r3, [fp, #-12]
.L3:
        ldr     r3, [fp, #-12]
        cmp     r3, #9
        bgt     .L2
        ldr     r1, [fp, #-8]
        ldr     r0, .L5
        bl      _ZNSolsEi
        mov     r3, r0
        ldr     r1, .L5+4
        mov     r0, r3
        bl      _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
        ldr     r3, [fp, #-8]
        sub     r3, r3, #2
        mov     r1, r3
        ldr     r0, .L5
        bl      _ZNSolsEi
        mov     r3, r0
        ldr     r1, .L5+4
        mov     r0, r3
          bl      _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
        ldr     r3, [fp, #-8]
        sub     r3, r3, #4
        mov     r1, r3
        ldr     r0, .L5
        bl      _ZNSolsEi
        mov     r3, r0
        ldr     r1, .L5+4
        mov     r0, r3
        bl      _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
        ldr     r3, [fp, #-8]
        sub     r3, r3, #6
        mov     r1, r3
        ldr     r0, .L5
        bl      _ZNSolsEi
        mov     r3, r0
        ldr     r1, .L5+4
        mov     r0, r3
        bl      _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
        ldr     r3, [fp, #-8]
        sub     r3, r3, #8
        mov     r1, r3
        .end
        
        
	
        Trabajo2.2
        //Cuevas Martinez Adrian de Jesus 19211623
        .arch armv6
	.eabi_attribute 28, 1
	.eabi_attribute 20, 1
	.eabi_attribute 21, 1
	.eabi_attribute 23, 3
	.eabi_attribute 24, 1
	.eabi_attribute 25, 1
	.eabi_attribute 26, 2
	.eabi_attribute 30, 6
	.eabi_attribute 34, 1
	.eabi_attribute 18, 4
	.file	"Ejercicio2.2.c"
	.text
	.section	.rodata
	.align	2
	.type	_ZStL19piecewise_construct, %object
	.size	_ZStL19piecewise_construct, 1
_ZStL19piecewise_construct:
	.space	1
	.local	_ZStL8__ioinit
	.comm	_ZStL8__ioinit,1,4
	.text
	.align	2
	.global	main
	.arch armv6
	.syntax unified
	.arm
	.fpu vfp
	.type	main, %function
main:
	.fnstart
.LFB1512:
	@ args = 0, pretend = 0, frame = 8
	@ frame_needed = 1, uses_anonymous_args = 0
	@ link register save eliminated.
	str	fp, [sp, #-4]!
	add	fp, sp, #0
	sub	sp, sp, #12
	mov	r3, #0
	str	r3, [fp, #-8]
	mov	r3, #0
	mov	r0, r3
	add	sp, fp, #0
	@ sp needed
	ldr	fp, [sp], #4
	bx	lr
	.cantunwind
	.fnend
	.size	main, .-main
	.align	2
	.syntax unified
	.arm
	.fpu vfp
	.type	_Z41__static_initialization_and_destruction_0ii, %function
_Z41__static_initialization_and_destruction_0ii:
	.fnstart
.LFB1993:
	@ args = 0, pretend = 0, frame = 8
	@ frame_needed = 1, uses_anonymous_args = 0
	push	{fp, lr}
	add	fp, sp, #4
	sub	sp, sp, #8
	str	r0, [fp, #-8]
	str	r1, [fp, #-12]
	ldr	r3, [fp, #-8]
	cmp	r3, #1
	bne	.L5
	ldr	r3, [fp, #-12]
	ldr	r2, .L6
	cmp	r3, r2
	bne	.L5
	ldr	r0, .L6+4
	bl	_ZNSt8ios_base4InitC1Ev
	ldr	r2, .L6+8
	ldr	r1, .L6+12
	ldr	r0, .L6+4
	bl	__aeabi_atexit
.L5:
	nop
	sub	sp, fp, #4
	@ sp needed
	pop	{fp, pc}
.L7:
	.align	2
.L6:
	.word	65535
	.word	_ZStL8__ioinit
	.word	__dso_handle
	.word	_ZNSt8ios_base4InitD1Ev
	.cantunwind
	.fnend
	.size	_Z41__static_initialization_and_destruction_0ii, .-_Z41__static_initialization_and_destruction_0ii
	.align	2
	.syntax unified
	.arm
	.fpu vfp
	.type	_GLOBAL__sub_I_main, %function
_GLOBAL__sub_I_main:
	.fnstart
.LFB1994:
	@ args = 0, pretend = 0, frame = 0
	@ frame_needed = 1, uses_anonymous_args = 0
	push	{fp, lr}
	add	fp, sp, #4
	ldr	r1, .L9
	mov	r0, #1
	bl	_Z41__static_initialization_and_destruction_0ii
	pop	{fp, pc}
.L10:
	.align	2
.L9:
	.word	65535
	.cantunwind
	.fnend
	.size	_GLOBAL__sub_I_main, .-_GLOBAL__sub_I_main
	.section	.init_array,"aw"
	.align	2
	.word	_GLOBAL__sub_I_main
	.hidden	__dso_handle
	.ident	"GCC: (Raspbian 8.3.0-6+rpi1) 8.3.0"
	.section	.note.GNU-stack,"",%progbits
  
  
  
  
  Ejercicio2.4
  //Cuevas Martinez Adrian de Jesus 19211623
	.eabi_attribute 28, 1
	.eabi_attribute 20, 1
	.eabi_attribute 21, 1
	.eabi_attribute 23, 3
	.eabi_attribute 24, 1
	.eabi_attribute 25, 1
	.eabi_attribute 26, 2
	.eabi_attribute 30, 6
	.eabi_attribute 34, 1
	.eabi_attribute 18, 4
	.file	"Trabajo2.4.c"
	.text
	.section	.rodata
	.align	2
	.type	_ZStL19piecewise_construct, %object
	.size	_ZStL19piecewise_construct, 1
_ZStL19piecewise_construct:
	.space	1
	.local	_ZStL8__ioinit
	.comm	_ZStL8__ioinit,1,4
	.align	2
.LC0:
	.ascii	"En %d hubo olimpiadas\012\000"
	.align	2
.LC1:
	.ascii	"En %d hubo mundial de futbol\012\000"
	.align	2
.LC2:
	.ascii	"En %d no paso nada\012\000"
	.text
	.align	2
	.global	main
	.arch armv6
	.syntax unified
	.arm
	.fpu vfp
	.type	main, %function
main:
	.fnstart
.LFB1512:
	@ args = 0, pretend = 0, frame = 8
	@ frame_needed = 1, uses_anonymous_args = 0
	push	{fp, lr}
	.save {fp, lr}
	.setfp fp, sp, #4
	add	fp, sp, #4
	.pad #8
	sub	sp, sp, #8
	ldr	r3, .L10
	str	r3, [fp, #-8]
.L7:
	ldr	r3, [fp, #-8]
	ldr	r2, .L10+4
	cmp	r3, r2
	bgt	.L2
	ldr	r3, [fp, #-8]
	and	r3, r3, #3
	cmp	r3, #0
	beq	.L3
	cmp	r3, #2
	beq	.L4
	b	.L9
.L3:
	ldr	r1, [fp, #-8]
	ldr	r0, .L10+8
	bl	printf
	b	.L6
.L4:
	ldr	r1, [fp, #-8]
	ldr	r0, .L10+12
	bl	printf
	b	.L6
.L9:
	ldr	r1, [fp, #-8]
	ldr	r0, .L10+16
	bl	printf
.L6:
	ldr	r3, [fp, #-8]
	add	r3, r3, #1
	str	r3, [fp, #-8]
	b	.L7
.L2:
	mov	r3, #0
	mov	r0, r3
	sub	sp, fp, #4
	@ sp needed
	pop	{fp, pc}
.L11:
	.align	2
.L10:
	.word	1950
	.word	2014
	.word	.LC0
	.word	.LC1
	.word	.LC2
	.fnend
	.size	main, .-main
	.align	2
	.syntax unified
	.arm
	.fpu vfp
	.type	_Z41__static_initialization_and_destruction_0ii, %function
_Z41__static_initialization_and_destruction_0ii:
	.fnstart
.LFB1993:
	@ args = 0, pretend = 0, frame = 8
	@ frame_needed = 1, uses_anonymous_args = 0
	push	{fp, lr}
	add	fp, sp, #4
	sub	sp, sp, #8
	str	r0, [fp, #-8]
	str	r1, [fp, #-12]
	ldr	r3, [fp, #-8]
	cmp	r3, #1
	bne	.L14
	ldr	r3, [fp, #-12]
	ldr	r2, .L15
	cmp	r3, r2
	bne	.L14
	ldr	r0, .L15+4
	bl	_ZNSt8ios_base4InitC1Ev
	ldr	r2, .L15+8
	ldr	r1, .L15+12
	ldr	r0, .L15+4
	bl	__aeabi_atexit
.L14:
	nop
	sub	sp, fp, #4
	@ sp needed
	pop	{fp, pc}
.L16:
	.align	2
.L15:
	.word	65535
	.word	_ZStL8__ioinit
	.word	__dso_handle
	.word	_ZNSt8ios_base4InitD1Ev
	.cantunwind
	.fnend
	.size	_Z41__static_initialization_and_destruction_0ii, .-_Z41__static_initialization_and_destruction_0ii
	.align	2
	.syntax unified
	.arm
	.fpu vfp
	.type	_GLOBAL__sub_I_main, %function
_GLOBAL__sub_I_main:
	.fnstart
.LFB1994:
	@ args = 0, pretend = 0, frame = 0
	@ frame_needed = 1, uses_anonymous_args = 0
	push	{fp, lr}
	add	fp, sp, #4
	ldr	r1, .L18
	mov	r0, #1
	bl	_Z41__static_initialization_and_destruction_0ii
	pop	{fp, pc}
.L19:
	.align	2
.L18:
	.word	65535
	.cantunwind
	.fnend
	.size	_GLOBAL__sub_I_main, .-_GLOBAL__sub_I_main
	.section	.init_array,"aw"
	.align	2
	.word	_GLOBAL__sub_I_main
	.hidden	__dso_handle
	.ident	"GCC: (Raspbian 8.3.0-6+rpi1) 8.3.0"
	.section	.note.GNU-stack,"",%progbits
  
        
        
        Ejercicio3.1
        //Cuevas Martínez Adrián de Jesús 19211623
        //Devolver el minimo de una lista de numeros en ensamblador
        .arco armv6
	.eabi_atributo 28 , 1
	.eabi_atributo 20 , 1
	.eabi_atributo 21 , 1
	.eabi_atributo 23 , 3
	.eabi_atributo 24 , 1
	.eabi_atributo 25 , 1
	.eabi_atributo 26 , 2
	.eabi_atributo 30 , 6
	.eabi_atributo 34 , 1
	.eabi_atributo 18 , 4
	.file 	"Ejercicio3.1.c"
	.texto
	.alinear 	2
	.global_Z6minimoPii 	_
	.arco armv6
	.sintaxis unificada
	.brazo
	.fpu vfp
	.type 	_Z6minimoPii, %función
_Z6minimoPii:
	.fnstart
.LFB0:
	@ args = 0 , pretender = 0 , marco = 16
	@ marco_necesario = 1 , utiliza_argumentos_anónimos = 0
	@ enlace registro guardar eliminado.
	str 	fp, [sp, #-4]!
	agregar 	fp, sp, #0
	sub 	sp, sp, #20
	cadena 	r0, [fp, #-16]
	str 	r1, [fp, #-20]
	ldr r3, [fp, #-16]
	ldr r3, [r3]
	str 	r3, [fp, #-12]
	movimiento 	r3, #1
	str 	r3, [fp, #-8]
.L4:
	ldr r2, [fp, #-8]
	ldr r3, [fp, #-20]
	cmp 	r2, r3
	bge .L2
	ldr r3, [fp, #-8]
	LSL 	r3, r3, #2
	ldr r2, [fp, #-16]
	suma 	r3, r2, r3
	ldr r3, [r3]
	ldrr2, [fp, #-12]
	cmp 	r2, r3
	ble .L3
	ldr r3, [fp, #-8]
	LSL 	r3, r3, #2
	ldr r2, [fp, #-16]
	suma 	r3, r2, r3
	ldr r3, [r3]
	str 	r3, [fp, #-12]
.L3:
	ldr r3, [fp, #-8]
	suma 	r3, r3, #1
	str 	r3, [fp, #-8]
	b .L4
.L2:
	ldr r3, [fp, #-12]
	movimiento 	r0, r3
	añadir 	sp, fp, #0
	@sp necesario
	ldrfp, [sp], #4
	bx lr
	.cantunwind
	.fnend
	.tamaño 	_Z6minimoPii, .-_Z6minimoPii
	.ident 	"CCG: (Raspbian 8.3.0-6+rpi1) 8.3.0"
	.section 	.note.GNU-stack,"",%progbits
  
  
  
  
  Ejercicio3.2.1
  //Cuevas Martínez Adrián de Jesús
//Media aritmetica
  .arco armv6
	.eabi_atributo 28 , 1
	.eabi_atributo 20 , 1
	.eabi_atributo 21 , 1
	.eabi_atributo 23 , 3
	.eabi_atributo 24 , 1
	.eabi_atributo 25 , 1
	.eabi_atributo 26 , 2
	.eabi_atributo 30 , 6
	.eabi_atributo 34 , 1
	.eabi_atributo 18 , 4
	.file 	"Ejercicio3.2.1.c"
	.texto
	.sección 	.rodata
	.alinear 	2
	.type 	_ZStL19piecewise_construct, %objeto
	.size 	_ZStL19piecewise_construct, 1
_ZStL19piecewise_construct:
	.espacio 	1
	.local 	_ZStL8__ioinit
	.comm 	_ZStL8__ioinit, 1 , 4
	.alinear 	2
.LC0:
	.ascii 	"El resultado es: \000"
	.texto
	.alinear 	2
	.global_Z10Iteracion1ii 	_
	.arco armv6
	.sintaxis unificada
	.brazo
	.fpu vfp
	.type 	_Z10Iteracion1ii, %función
_Z10Iteracion1ii:
	.fnstart
.LFB1512:
	@ args = 0 , pretender = 0 , marco = 16
	@ marco_necesario = 1 , utiliza_argumentos_anónimos = 0
	empujar 	{fp, lr}
	.guardar {fp, lr}
	.setfp fp, sp, #4
	agregar 	fp, sp, #4
	.almohadilla #16
	sub 	sp, sp, #16
	cadena 	r0, [fp, #-16]
	str 	r1, [fp, #-20]
	ldr r2, [fp, #-16]
	ldr r3, [fp, #-20]
	suma 	r3, r2, r3
	lsr r2, r3, #31
	suma 	r3, r2, r3
	asr r3, r3, #1
	str 	r3, [fp, #-8]
	ldr r1, .L2
	ldr r0, .L2+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	movimiento 	r3, r0
	ldr r1, [fp, #-8]
	movimiento 	r0, r3
	bl _ZNSolsEi
	movimiento 	r3, r0
	ldr r1, .L2+ 8
	movimiento 	r0, r3
	bl _ZNSolsEPFRSoS_E
	nop
	sub 	sp, fp, #4
	@sp necesario
	estallar 	{fp, pc}
.L3:
	.alinear 	2
.L2:
	.palabra 	.LC0
	.palabra 	_ZSt4cout
	.palabra 	_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_
	.fnend
	.size 	_Z10Iteracion1ii, .-_Z10Iteracion1ii
	.alinear 	2
	.sintaxis unificada
	.brazo
	.fpu vfp
	.type 	_ZL10Iteracion2ii, %funcion
_ZL10Iteracion2ii:
	.fnstart
.LFB1513:
	@ args = 0 , pretender = 0 , marco = 16
	@ marco_necesario = 1 , utiliza_argumentos_anónimos = 0
	empujar 	{fp, lr}
	.guardar {fp, lr}
	.setfp fp, sp, #4
	agregar 	fp, sp, #4
	.almohadilla #16
	sub 	sp, sp, #16
	cadena 	r0, [fp, #-16]
	str 	r1, [fp, #-20]
	ldr r2, [fp, #-16]
	ldr r3, [fp, #-20]
	suma 	r3, r2, r3
	lsr r2, r3, #31
	suma 	r3, r2, r3
	asr r3, r3, #1
	str 	r3, [fp, #-8]
	ldr r1, .L5
	ldr r0, .L5+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	movimiento 	r3, r0
	ldr r1, [fp, #-8]
	movimiento 	r0, r3
	bl _ZNSolsEi
	movimiento 	r3, r0
	ldr r1, .L5+ 8
	movimiento 	r0, r3
	bl _ZNSolsEPFRSoS_E
	nop
	sub 	sp, fp, #4
	@sp necesario
	estallar 	{fp, pc}
.L6:
	.alinear 	2
.L5:
	.palabra 	.LC0
	.palabra 	_ZSt4cout
	.palabra 	_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_
	.fnend
	.size 	_ZL10Iteracion2ii, .-_ZL10Iteracion2ii
	.alinear 	2
	.sintaxis unificada
	.brazo
	.fpu vfp
	.type 	_ZL10Iteracion3ii, %función
_ZL10Iteracion3ii:
	.fnstart
.LFB1514:
	@ args = 0 , pretender = 0 , marco = 16
	@ marco_necesario = 1 , utiliza_argumentos_anónimos = 0
	empujar 	{fp, lr}
	.guardar {fp, lr}
	.setfp fp, sp, #4
	agregar 	fp, sp, #4
	.almohadilla #16
	sub 	sp, sp, #16
	cadena 	r0, [fp, #-16]
	str 	r1, [fp, #-20]
	ldr r2, [fp, #-16]
	ldr r3, [fp, #-20]
	suma 	r3, r2, r3
	lsr r2, r3, #31
	suma 	r3, r2, r3
	asr r3, r3, #1
	str 	r3, [fp, #-8]
	ldr r1, .L8
	ldr r0, .L8+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	movimiento 	r3, r0
	ldr r1, [fp, #-8]
	movimiento 	r0, r3
	bl _ZNSolsEi
	movimiento 	r3, r0
	ldr r1, .L8+ 8
	movimiento 	r0, r3
	bl _ZNSolsEPFRSoS_E
	nop
	sub 	sp, fp, #4
	@sp necesario
	estallar 	{fp, pc}
.L9:
	.alinear 	2
.L8:
	.palabra 	.LC0
	.palabra 	_ZSt4cout
	.palabra 	_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_
	.fnend
	.size 	_ZL10Iteracion3ii, .-_ZL10Iteracion3ii
	.alinear 	2
	.sintaxis unificada
	.brazo
	.fpu vfp
	.type 	_ZL10Iteracion4ii, %función
_ZL10Iteracion4ii:
	.fnstart
.LFB1515:
	@ args = 0 , pretender = 0 , marco = 16
	@ marco_necesario = 1 , utiliza_argumentos_anónimos = 0
	empujar 	{fp, lr}
	.guardar {fp, lr}
	.setfp fp, sp, #4
	agregar 	fp, sp, #4
	.almohadilla #16
	sub 	sp, sp, #16
	cadena 	r0, [fp, #-16]
	str 	r1, [fp, #-20]
	ldr r2, [fp, #-16]
	ldr r3, [fp, #-20]
	suma 	r3, r2, r3
	lsr r2, r3, #31
	suma 	r3, r2, r3
	asr r3, r3, #1
	str 	r3, [fp, #-8]
	ldr r1, .L11
	ldr r0, .L11+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	movimiento 	r3, r0
	ldr r1, [fp, #-8]
	movimiento 	r0, r3
	bl _ZNSolsEi
	movimiento 	r3, r0
	ldr r1, .L11+ 8
	movimiento 	r0, r3
	bl _ZNSolsEPFRSoS_E
	nop
	sub 	sp, fp, #4
	@sp necesario
	estallar 	{fp, pc}
.L12:
	.alinear 	2
.L11:
	.palabra 	.LC0
	.palabra 	_ZSt4cout
	.palabra 	_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_
	.fnend
	.size 	_ZL10Iteracion4ii, .-_ZL10Iteracion4ii
	.alinear 	2
	.sintaxis unificada
	.brazo
	.fpu vfp
	.type 	_ZL10Iteracion5ii, %función
_ZL10Iteracion5ii:
	.fnstart
.LFB1516:
	@ args = 0 , pretender = 0 , marco = 16
	@ marco_necesario = 1 , utiliza_argumentos_anónimos = 0
	empujar 	{fp, lr}
	.guardar {fp, lr}
	.setfp fp, sp, #4
	agregar 	fp, sp, #4
	.almohadilla #16
	sub 	sp, sp, #16
	cadena 	r0, [fp, #-16]
	str 	r1, [fp, #-20]
	ldr r2, [fp, #-16]
	ldr r3, [fp, #-20]
	suma 	r3, r2, r3
	lsr r2, r3, #31
	suma 	r3, r2, r3
	asr r3, r3, #1
	str 	r3, [fp, #-8]
	ldr r1, .L14
	ldr r0, .L14+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	movimiento 	r3, r0
	ldr r1, [fp, #-8]
	movimiento 	r0, r3
	bl _ZNSolsEi
	movimiento 	r3, r0
	ldr r1, .L14+ 8
	movimiento 	r0, r3
	bl _ZNSolsEPFRSoS_E
	nop
	sub 	sp, fp, #4
	@sp necesario
	estallar 	{fp, pc}
.L15:
	.alinear 	2
.L14:
	.palabra 	.LC0
	.palabra 	_ZSt4cout
	.palabra 	_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_
	.fnend
	.size 	_ZL10Iteracion5ii, .-_ZL10Iteracion5ii
	.sección 	.rodata
	.alinear 	2
.LC1:
	.ascii 	"dar los números para la primera iteración:\000"
	.alinear 	2
.LC2:
	.ascii 	"ingresa el primer numero: \000"
	.alinear 	2
.LC3:
	.ascii 	"ingresa el segundo número: \000"
	.alinear 	2
.LC4:
	.ascii 	"dar los numeros para la segunda iteracion:\000"
	.alinear 	2
.LC5:
	.ascii 	"dar los números para la tercera iteración:\000"
	.alinear 	2
.LC6:
	.ascii 	"dar los numeros para la cuarta iteracion:\000"
	.alinear 	2
.LC7:
	.ascii 	"dar los números para la quinta iteración:\000"
	.texto
	.alinear 	2
	.global 	principal
	.sintaxis unificada
	.brazo
	.fpu vfp
	.tipo 	principal, %función
principal:
	.fnstart
.LFB1517:
	@ args = 0 , pretender = 0 , marco = 40
	@ marco_necesario = 1 , utiliza_argumentos_anónimos = 0
	empujar 	{fp, lr}
	.guardar {fp, lr}
	.setfp fp, sp, #4
	agregar 	fp, sp, #4
	.almohadilla #40
	sub 	sp, sp, #40
	ldr r1, .L18
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	ldr r1, .L18+ 8
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #8
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r1, .L18+ 16
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #12
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r1, .L18+ 20
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	ldr r1, .L18+ 8
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #16
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r1, .L18+ 16
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #20
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r1, .L18+ 24
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	ldr r1, .L18+ 8
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #24
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r1, .L18+ 16
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #28
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r1, .L18+ 28
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	ldr r1, .L18+ 8
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #32
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r1, .L18+ 16
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #36
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r1, .L18+ 32
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	ldr r1, .L18+ 8
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #40
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r1, .L18+ 16
	ldr r0, .L18+ 4
	bl _ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
	sub 	r3, fp, #44
	mover 	r1, r3
	ldr r0, .L18+ 12
	bl _ZNSirsERi
	ldr r3, [fp, #-8]
	ldrr2, [fp, #-12]
	mover 	r1, r2
	movimiento 	r0, r3
	bl_Z10Iteracion1ii
	ldr r3, [fp, #-16]
	ldr r2, [fp, #-20]
	mover 	r1, r2
	movimiento 	r0, r3
	bl _ZL10Iteracion2ii
	ldr r3, [fp, #-24]
	ldr r2, [fp, #-28]
	mover 	r1, r2
	movimiento 	r0, r3
	bl_ZL10Iteracion3ii
	ldr r3, [fp, #-32]
	ldrr2, [fp, #-36]
	mover 	r1, r2
	movimiento 	r0, r3
	bl_ZL10Iteracion4ii
	ldr r3, [fp, #-40]
	ldrr2, [fp, #-44]
	mover 	r1, r2
	movimiento 	r0, r3
	bl _ZL10Iteracion5ii
	ldr r1, .L18+ 36
	ldr r0, .L18+ 4
	bl _ZNSolsEPFRSoS_E
	movimiento 	r3, r0
	ldr r1, .L18+ 36
	movimiento 	r0, r3
	bl _ZNSolsEPFRSoS_E
	movimiento 	r3, #0
	movimiento 	r0, r3
	sub 	sp, fp, #4
	@sp necesario
	estallar 	{fp, pc}
.L19:
	.alinear 	2
.L18:
	.palabra 	.LC1
	.palabra 	_ZSt4cout
	.palabra 	.LC2
	.palabra 	_ZSt3cin
	.palabra 	.LC3
	.palabra 	.LC4
	.palabra 	.LC5
	.palabra 	.LC6
	.palabra 	.LC7
	.palabra 	_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_
	.fnend
	.tamaño 	principal, .-principal
	.alinear 	2
	.sintaxis unificada
	.brazo
	.fpu vfp
	.type 	_Z41__static_initialization_and_destruction_0ii, %función
_Z41__inicialización_estática_y_destrucción_0ii:
	.fnstart
.LFB2006:
	@ args = 0 , pretender = 0 , marco = 8
	@ marco_necesario = 1 , utiliza_argumentos_anónimos = 0
	empujar 	{fp, lr}
	agregar 	fp, sp, #4
	sub 	sp, sp, #8
	str 	r0, [fp, #-8]
	str 	r1, [fp, #-12]
	ldr r3, [fp, #-8]
	cmpr3 	, #1
	bne .L22
	ldr r3, [fp, #-12]
	ldr r2, .L23
	cmp 	r3, r2
	bne .L22
	ldr r0, .L23+ 4
	bl _ZNSt8ios_base4InitC1Ev
	ldr r2, .L23+ 8
	ldr r1, .L23+ 12
	ldr r0, .L23+ 4
	bl __aeabi_atexit
.L22:
	nop
	sub 	sp, fp, #4
	@sp necesario
	estallar 	{fp, pc}
.L24:
	.alinear 	2
.L23:
	.palabra 	65535
	.palabra 	_ZStL8__ioinit
	.palabra 	__dso_handle
	.palabra 	_ZNSt8ios_base4InitD1Ev
	.cantunwind
	.fnend
	.size 	_Z41__static_initialization_and_destruction_0ii, .-_Z41__static_initialization_and_destruction_0ii
	.alinear 	2
	.sintaxis unificada
	.brazo
	.fpu vfp
	.type 	_GLOBAL__sub_I__Z10Iteracion1ii, %función
_GLOBAL__sub_I__Z10Iteracion1ii:
	.fnstart
.LFB2007:
	@ args = 0 , pretender = 0 , marco = 0
	@ marco_necesario = 1 , utiliza_argumentos_anónimos = 0
	empujar 	{fp, lr}
	agregar 	fp, sp, #4
	ldr r1, .L26
	movimiento 	r0, #1
	bl _Z41__static_initialization_and_destruction_0ii
	estallar 	{fp, pc}
.L27:
	.alinear 	2
.L26:
	.palabra 	65535
	.cantunwind
	.fnend
	.size 	_GLOBAL__sub_I__Z10Iteracion1ii, .-_GLOBAL__sub_I__Z10Iteracion1ii
	.sección 	.init_array, "aw"
	.alinear 	2
	.word 	_GLOBAL__sub_I__Z10Iteracion1ii
	.hidden 	__dso_handle
	.ident 	"CCG: (Raspbian 8.3.0-6+rpi1) 8.3.0"
	.section 	.note.GNU-stack,"",%progbits
  




  Ejercicio3.2
  //Cuevas Martinez Adrian de Jesus 19211623
//Minimo de un vector

	.arch armv6
	.eabi_attribute 28, 1
	.eabi_attribute 20, 1
	.eabi_attribute 21, 1
	.eabi_attribute 23, 3
	.eabi_attribute 24, 1
	.eabi_attribute 25, 1
	.eabi_attribute 26, 2
	.eabi_attribute 30, 6
	.eabi_attribute 34, 1
	.eabi_attribute 18, 4
	.file	"Ejercicio3.2.c"
	.text
	.global	a
	.data
	.align	2
	.type	a, %object
	.size	a, 32
a:
        .global
	.word	8
	.word	10
	.word	-3
	.word	4
	.word	-5
	.word	50
	.word	2
	.word	3
	.section	.rodata
	.align	2
.LC0:
	.ascii	"min is %d\012\000"
	.align	2
.LC1:
	.ascii	"pause\000"
	.text
	.align	2
	.global	main
	.arch armv6
	.syntax unified
	.arm
	.fpu vfp
	.type	main, %function
main:
	.fnstart
.LFB13:
	@ args = 0, pretend = 0, frame = 8
	@ frame_needed = 1, uses_anonymous_args = 0
	push	{fp, lr}
	.save {fp, lr}
	.setfp fp, sp, #4
	add	fp, sp, #4
	.pad #8
	sub	sp, sp, #8
	ldr	r3, .L6
	ldr	r3, [r3]
	str	r3, [fp, #-8]
	mov	r3, #0
	str	r3, [fp, #-12]
.L4:
	ldr	r3, [fp, #-12]
	cmp	r3, #4
	bgt	.L2
	ldr	r2, .L6
	ldr	r3, [fp, #-12]
	ldr	r3, [r2, r3, lsl #2]
	ldr	r2, [fp, #-8]
	cmp	r2, r3
	ble	.L3
	ldr	r2, .L6
	ldr	r3, [fp, #-12]
	ldr	r3, [r2, r3, lsl #2]
	str	r3, [fp, #-8]
.L3:
	ldr	r3, [fp, #-12]
	add	r3, r3, #1
	str	r3, [fp, #-12]
	b	.L4
.L2:
	ldr	r1, [fp, #-8]
	ldr	r0, .L6+4
	bl	printf
	ldr	r0, .L6+8
	bl	system
	mov	r3, #0
	mov	r0, r3
	sub	sp, fp, #4
	@ sp needed
	pop	{fp, pc}
.L7:
	.align	2
.L6:
	.word	a
	.word	.LC0
	.word	.LC1
	.fnend
	.size	main, .-main
	.ident	"GCC: (Raspbian 8.3.0-6+rpi1) 8.3.0"
	.section	.note.GNU-stack,"",%progbits



