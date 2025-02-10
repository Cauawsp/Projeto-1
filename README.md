import socket  

# Configuração do servidor
HOST = '0.0.0.0'  # Escuta em todas as interfaces
PORT = 12345      # Porta de comunicação

# Criando o socket do servidor
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind((HOST, PORT))
server_socket.listen(5)

print(f"Servidor escutando na porta {PORT}...")

while True:
    conn, addr = server_socket.accept()
    print(f"Conexão recebida de {addr}")
    
    data = conn.recv(1024).decode()
    print(f"Mensagem recebida: {data}")
    
    conn.sendall(b"Mensagem recebida com sucesso!")  
    conn.close()
