from flask import Flask, request, jsonify
import time

app = Flask(__name__)

# --- BANCO DE DADOS SIMULADO DE CHAVES ---
# Chave: [Data de Expiração (Timestamp UNIX), Status]
# Exemplo: 1735689600 é 1º de Janeiro de 2025
KEYS_DATABASE = {
    "CHAVE-TESTE-123": [1735689600, "active"],  # Válida até 2025
    "CHAVE-EXPIRADA-456": [1672531200, "expired"], # Expirada em 2023
    "CHAVE-NOVINHA-789": [time.time() + 86400, "active"] # Válida por mais 24h
}
# ------------------------------------------

@app.route('/api/verify', methods=['GET'])
def verify_key():
    # 1. Pega a chave enviada pelo script Lua
    key = request.args.get('key')
    
    if not key:
        return jsonify({"status": "error", "message": "Chave não fornecida."}), 400

    # 2. Verifica se a chave existe no "banco de dados"
    if key not in KEYS_DATABASE:
        return jsonify({"status": "invalid", "message": "Chave desconhecida."}), 200

    key_info = KEYS_DATABASE[key]
    expiry_time = key_info[0]
    current_status = key_info[1]
    
    # 3. Verifica a validade (se o status for ativo)
    if current_status == "active":
        if time.time() < expiry_time:
            # Chave válida e não expirada
            return jsonify({"status": "valid", "message": "Acesso concedido."}), 200
        else:
            # Chave expirou agora
            KEYS_DATABASE[key][1] = "expired" # Atualiza o status no DB (na vida real, isso seria persistente)
            return jsonify({"status": "expired", "message": "Chave expirada."}), 200
    
    # 4. Se o status já for 'expired' ou outro
    return jsonify({"status": current_status, "message": "Status da chave: " + current_status}), 200

if __name__ == '__main__':
    # Em produção, você usaria Gunicorn ou Waitress
    app.run(host='0.0.0.0', port=5000, debug=True)
