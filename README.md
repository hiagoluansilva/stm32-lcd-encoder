# STM32 LCD Encoder — Encoder com Display LCD I2C

🇧🇷 **Português** | 🇺🇸 [English](#english)

---

## Português

Leitura de encoder rotativo via TIM3 em modo encoder, exibindo a posição em tempo real em display LCD I2C no STM32F4xx.

### O que faz
- **TIM3** opera em modo encoder: conta pulsos A/B do encoder incremental
- Posição atual lida diretamente do registrador `TIM3->CNT`
- **LCD I2C** exibe o valor de contagem em tempo real
- Driver LCD implementado inline com `lcd_send_cmd` / `lcd_send_data`

### Código principal
```c
HAL_TIM_Encoder_Start(&htim3, TIM_CHANNEL_ALL);
lcd_init();

while (1) {
    i = TIM3->CNT;      // leitura direta do registrador
    // atualiza LCD com valor de i
}
```

### Mapa de pinos
| Pino | Função |
|---|---|
| PA6 / PA7 | TIM3 CH1/CH2 — encoder A/B |
| I2C SCL | Clock I2C para LCD |
| I2C SDA | Dados I2C para LCD |

### Microcontrolador
STM32F4xx — Atollic TrueSTUDIO

---

## English

Rotary encoder reading via TIM3 in encoder mode, displaying position in real time on an I2C LCD on STM32F4xx.

### What it does
- **TIM3** runs in encoder mode: counts A/B pulses from incremental encoder
- Current position read directly from `TIM3->CNT` register
- **I2C LCD** displays the count value in real time
- LCD driver implemented inline with `lcd_send_cmd` / `lcd_send_data`

### Main code
```c
HAL_TIM_Encoder_Start(&htim3, TIM_CHANNEL_ALL);
lcd_init();

while (1) {
    i = TIM3->CNT;      // direct register read
    // update LCD with value of i
}
```

### Pin map
| Pin | Function |
|---|---|
| PA6 / PA7 | TIM3 CH1/CH2 — encoder A/B |
| I2C SCL | I2C clock for LCD |
| I2C SDA | I2C data for LCD |

### MCU
STM32F4xx — Atollic TrueSTUDIO
