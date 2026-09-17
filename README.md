# POOL de liquidez V2 de ZAARD ⚡ — Official Repository

Welcome to the official repository.

---

## 📌 Direcciones de Contratos (Smart Contracts)

* **Contrato del Token ZAARD:** `0x973ba2c1dccd0820f1e026d6b1f01c55c4085d38`
* **Contrato de Pool de Liquidez (ZAARD/WBNB):** `0x046dD1d5C62a6DFFAfAA4886B3004Fed7d409Dd3`

---

## 📐 Especificaciones Técnicas: PancakePair (ZARD/WBNB)

Este contrato implementa el par de liquidez estándar de PancakeSwap V2. La integridad del mercado se mantiene mediante el invariante de producto constante.

### Invariante del Producto Constante
El equilibrio del pool se rige por la ecuación fundamental de Uniswap:

$$x \cdot y = k$$

**Donde:**
* $x$: Reserva del Token 0 (ZAARD).
* $y$: Reserva del Token 1 (WBNB).
* $k$: Producto constante que debe permanecer inalterado o aumentar tras cada operación.

---

## ⚙️ Métodos Críticos de Ejecución

| Función | Descripción Técnica | Modificador |
| :--- | :--- | :--- |
| `mint(address to)` | Emite tokens LP a cambio de aportar liquidez al pool. | `lock` |
| `burn(address to)` | Quema tokens LP y retira la participación proporcional. | `lock` |
| `swap(...)` | Ejecuta el intercambio de tokens bajo el modelo de $k$. | `lock` |
| `sync()` | Sincroniza las reservas del contrato con los saldos reales. | `lock` |

---

## 🛡️ Mecanismos de Seguridad

* **Reentrancy Guard:** El modificador `lock` impide ataques de reentrada durante la ejecución de las funciones críticas (`mint`, `burn`, `swap`).
* **Validación de Saldo (K):** En la función `swap`, se aplica la verificación del invariante: $balance_0 \cdot balance_1 \cdot 10000^2 \geq reserve_0 \cdot reserve_1 \cdot 10000^2$. Esto garantiza que la comisión del 0.25% se mantenga dentro del pool.

---

## 📊 Lógica de Precios

El contrato utiliza acumuladores de precio para permitir la creación de **Oráculos de Precio (TWAP)**:
* `price0CumulativeLast`: Suma del precio del token 0 multiplicado por el tiempo transcurrido.
* `price1CumulativeLast`: Suma del precio del token 1 multiplicado por el tiempo transcurrido.

---

> **Nota:** Este contrato es inmutable y estándar en el ecosistema DeFi. Toda liquidez está asegurada mediante el protocolo.
---

## 🌐 Our Official Digital Presence

Stay connected with the true source of ZAARD innovation.

* **🏠 Official Website:** [https://figueredo56.github.io/zaard-official/](https://figueredo56.github.io/zaard-official/)
* **🐦 Official X (Twitter):** [@ZAARD_666](https://x.com/ZAARD_666)
* **💰 Binance User Profile (Founder/DAO):** [View on Binance](https://account.binance.com/register?ref=776427353&?registerChannel=user_center) (User ref: 776427353)
## 👤 Founder & Lead Developer
Desarrollado por **Aracelis (Panga)** - Founder de ZAARD INNOVATION.

[<img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />](https://www.linkedin.com/in/aracelis-figueredo-45284a408?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)

