![logo zaird](https://raw.githubusercontent.com/figueredo56/ZIRD-infinito-/178cb6d8cae49079bf492586182ac1b238e67e5e/CC_20260522_154445.svg)

# POOL de liquidez V2 de ZARD ⚡ — Official Repository

Welcome to the official repository

# Especificaciones Técnicas: PancakePair (ZARD/WBNB)

Este contrato implementa el par de liquidez estándar de PancakeSwap V2. La integridad del mercado se mantiene mediante el invariante de producto constante.

## 📐 Invariante del Producto Constante
El equilibrio del pool se rige por la ecuación fundamental de Uniswap:

$$x \cdot y = k$$

Donde:
*   $x$: Reserva del Token 0 (ZARD).
*   $y$: Reserva del Token 1 (WBNB).
*   $k$: Producto constante que debe permanecer inalterado o aumentar tras cada operación.

## ⚙️ Métodos Críticos de Ejecución

| Función | Descripción Técnica | Modificador |
| :--- | :--- | :--- |
| `mint(address to)` | Emite tokens LP a cambio de aportar liquidez al pool. | `lock` |
| `burn(address to)` | Quema tokens LP y retira la participación proporcional. | `lock` |
| `swap(...)` | Ejecuta el intercambio de tokens bajo el modelo de $k$. | `lock` |
| `sync()` | Sincroniza las reservas del contrato con los saldos reales. | `lock` |

## 🛡 Mecanismos de Seguridad
*   **Reentrancy Guard**: El modificador `lock` impide ataques de reentrada durante la ejecución de las funciones críticas (`mint`, `burn`, `swap`).
*   **Validación de Saldo (K)**: En la función `swap`, se aplica la verificación del invariante:
    $$\text{balance}_{0, \text{adj}} \cdot \text{balance}_{1, \text{adj}} \geq \text{reserve}_0 \cdot \text{reserve}_1 \cdot 10000^2$$
    *Esto garantiza que la comisión del 0.25% se mantenga dentro del pool.*

## 🔢 Lógica de Precios
El contrato utiliza acumuladores de precio para permitir la creación de **Oráculos de Precio (TWAP)**:
*   `price0CumulativeLast`: Suma del precio del token 0 multiplicado por el tiempo transcurrido.
*   `price1CumulativeLast`: Suma del precio del token 1 multiplicado por el tiempo transcurrido.

---
*Nota: Este contrato es inmutable y estándar en el ecosistema DeFi. Toda liquidez está protegida por los contratos de bloqueo de PinkSale.*

---
---

[ZAIRD Token](https://app.binance.com/uni-qr/web3-token-details?utm_medium=share&tokenCA=0x84027d2b2f269bfd39598b0b074dbccf48634549&binanceChainId=56&chain=bsc)

---
---

## 🌐 Our Official Digital Presence

Stay connected with the true source of ZAARD innovation.

* **🏠 Official Website:** [https://figueredo56.github.io/zaard-official/](https://figueredo56.github.io/zaard-official/)
* **🐦 Official X (Twitter):** [@ZAARD_666](https://x.com/ZAARD_666)
* **💰 Binance User Profile (Founder/DAO):** [View on Binance](https://account.binance.com/register?ref=776427353&?registerChannel=user_center) (User ref: 776427353)
## 👤 Founder & Lead Developer
Desarrollado por **Aracelis (Panga)** - Founder de ZAARD INNOVATION.

[<img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />](https://www.linkedin.com/in/aracelis-figueredo-45284a408?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)

