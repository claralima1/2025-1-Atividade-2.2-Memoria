# Relatório: 
Clara Lima de Almeida 
(https://github.com/claralima1) 

## Resposta

### 1. Alocação Inicial com Best-Fit

Memória RAM: 64 KB  
Processos e seus tamanhos:
- P1: 20 KB
- P2: 15 KB
- P3: 25 KB
- P4: 10 KB
- P5: 18 KB

**Passo 1 - RAM Inicialmente Vazia**

Aplicando o algoritmo **Best-Fit**, que aloca o processo no menor espaço livre disponível que seja suficiente:

- **P1 (20 KB)** → Alocado no início da RAM: [0 - 20]
- **P2 (15 KB)** → Alocado no próximo espaço: [20 - 35]
- **P4 (10 KB)** → Alocado após P2: [35 - 45]
- **P5 (18 KB)** → Alocado após P4: [45 - 63] → *Espaço insuficiente (só 19 KB livres), mas P5 precisa de 18 KB, então ele entra aqui.*
- **P3 (25 KB)** → Não cabe nos espaços restantes → Será paginado

**Estado da RAM (Best-Fit):**
- [0 – 20] → P1
- [20 – 35] → P2
- [35 – 45] → P4
- [45 – 63] → P5
- [63 – 64] → Livre (1 KB restante)
- P3 permanece fora (irá para memória virtual)

---

### 2. Simular Memória Virtual (Paginação)

Como a RAM não é suficiente para todos os processos, utilizaremos paginação para armazenar **P3** parcialmente ou totalmente no disco.

Vamos dividir os processos em páginas de 4 KB (tamanho comum em sistemas reais).

**Tabela de Páginas (Exemplo com P3 sendo paginado):**

| Processo | Página | Localização |
|----------|--------|-------------|
| P1       | 0-4    | RAM         |
| P1       | 5      | RAM         |
| P2       | 0-3    | RAM         |
| P2       | 4      | RAM         |
| P4       | 0-2    | RAM         |
| P5       | 0-4    | RAM         |
| P5       | 5      | RAM         |
| P3       | 0-5    | Disco       |

P3 com 25 KB → requer 7 páginas (7 × 4 = 28 KB); todas vão para a memória virtual, pois não há espaço suficiente na RAM.

---

### 3. Desfragmentação da RAM

Após a desfragmentação, todos os processos são movidos para formar um bloco contíguo, eliminando fragmentação interna entre eles.

Antes da desfragmentação:

[0-20] → P1
[20-35] → P2
[35-45] → P4
[45-63] → P5


**RAM usada:**  
- P1: 20 KB  
- P2: 15 KB  
- P4: 10 KB  
- P5: 18 KB  
**Total usado: 63 KB**  
**Livre: 1 KB**

**Após desfragmentação:**

[0-20] → P1
[20-35] → P2
[35-45] → P4
[45-63] → P5