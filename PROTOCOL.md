# Aizora Protocol Specification v0.1 (MVP)

## 1. Общие сведения
- **Название**: Aizora (AIZ)
- **Модель учёта средств**: UTXO (Unspent Transaction Output)
- **Консенсус**: Proof-of-Work (PoW) на старте; гибридный PoW/PoS в будущих версиях
- **Алгоритм хеширования**: Blake3 (вместо SHA-256) — повышенная скорость, лучшая параллелизация
- **Целевое время блока**: 120 секунд (против 600 с у Bitcoin)
- **Награда за блок**: 50 AIZ, халвинг каждые 210 000 блоков
- **Максимальная эмиссия**: 21 000 000 AIZ (совместимо с привычными ожиданиями рынка)

---

## 2. Структура блока (Block Structure)

### 2.1 Заголовок блока (Block Header)
```rust
struct BlockHeader {
    version: u32,                 // Версия протокола
    prev_block_hash: [u8; 32],    // Хеш предыдущего блока
    merkle_root: [u8; 32],        // Корень дерева Меркла транзакций
    timestamp: u64,               // Unix timestamp (секунды)
    bits: u32,                    // Сложность (compact format)
    nonce: u64                    // Nonce для PoW
}
