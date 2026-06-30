

## Tailscale — VPN Mesh Privada

### O que é

Tailscale cria uma rede privada virtual entre seus dispositivos usando o protocolo WireGuard. Diferente de VPNs tradicionais, não há servidor central — cada dispositivo se conecta diretamente aos outros numa arquitetura mesh.

---

### Por que usar em segurança

- Acesso remoto seguro a servidores sem expor portas públicas
- Comunicação criptografada entre dispositivos da equipe
- Substitui VPNs corporativas complexas
- Funciona atrás de NAT e firewall sem configuração especial

---

### Comandos do módulo explicados

```bash
# Instala o Tailscale
curl -fsSL https://tailscale.com/install.sh | sh

# Habilita e inicia o serviço automaticamente no boot
sudo systemctl enable --now tailscaled

# Autentica na sua conta (abre link no navegador)
sudo tailscale up

# Mostra seu IP na rede Tailscale (sempre 100.x.x.x)
tailscale ip -4

# Lista todos os dispositivos conectados na sua rede
tailscale status
```

---

### Comandos adicionais úteis

```bash
# Desconectar da rede
sudo tailscale down

# Ativar como exit node (rotear tráfego pelo dispositivo)
sudo tailscale up --advertise-exit-node

# Ver logs de conexão
journalctl -u tailscaled
```

---

### Tailscale vs VPN tradicional

| | Tailscale | VPN tradicional |
|---|---|---|
| Arquitetura | Mesh (P2P) | Cliente-servidor |
| Configuração | Mínima | Complexa |
| Protocolo | WireGuard | OpenVPN / IPSec |
| Escala | Dispositivos pessoais/equipe | Corporativa |

