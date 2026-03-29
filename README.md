# stm32-lcd-encoder

LCD I2C com encoder rotativo no STM32F4xx usando STM32 HAL.

## Descrição

Projeto HAL que combina display LCD 16×2 via I2C com encoder rotativo. O driver LCD é implementado diretamente via `HAL_I2C_Master_Transmit` no protocolo de 4 bits, e o encoder é lido via timer em modo de captura.

## Hardware

- Microcontrolador: STM32F4xx
- Display: LCD 16×2 com I2C (endereço 0x4E / 0x27)
- Encoder: rotativo incremental
- Pinos I2C: PB8 (SCL), PB9 (SDA)

## Periféricos

| Periférico | Função |
|------------|--------|
| I2C1 | Display LCD |
| TIM3 | Leitura encoder (modo encoder) |
| USART2 | Debug serial |

## Driver LCD inline

```c
void lcd_send_cmd(char cmd);   // Envia comando
void lcd_send_data(char data); // Envia caractere
```

Protocolo de 4 bits via PCF8574 (expansor I2C).

## Estrutura

```
lcd_i2c_encoder/
├── Src/
│   ├── main.c       # LCD + encoder integrados
│   └── stm32f4xx_it.c
├── Inc/
└── Drivers/
```

## IDE

Atollic TrueSTUDIO 9.3 / STM32CubeIDE

## Escola

Centro Tecnológico Liberato — Novo Hamburgo/RS
