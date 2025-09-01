## Reconhecimento Facial (CPU/Colab) — Detecção + Embeddings + Galeria em Memória
- Pipeline de detecção e reconhecimento facial rodando 100% em CPU (Google Colab ou local), focado em simplicidade e reprodutibilidade:
- Detecção: MTCNN
- Embeddings: DeepFace (modelo Facenet512)
- Reconhecimento: comparação por similaridade cosseno com galeria em memória (sem criar recortes no disco)
- Diferencial: você pode rotular 4 pessoas de uma foto multipessoas (ordem esquerda→direita) e reconhecer sem precisar salvar imagens intermediárias.

## 🧱 Arquitetura
- Detecção: MTCNN encontra as faces e retorna bounding boxes.
- Pré-processamento: safe_crop com margem para enquadrar melhor a face.
- Embeddings: DeepFace/Facenet512 gera vetores (512D).
- Galeria em memória: dicionário {nome: embedding} criado a partir da mesma foto multipessoas (ordem esquerda→direita).
- Reconhecimento: cosseno entre embedding detectado e os da galeria; aplica limiar (threshold).
