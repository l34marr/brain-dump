確認 ollama 成功執行
```
$ grep ExecStart /etc/systemd/system/ollama.service
ExecStart=/usr/local/bin/ollama serve

$ ps aux | grep ollama
ollama     32448  0.0  0.2 1862248 45984 ?       Ssl  01:46   0:01 /usr/local/bin/ollama serve
```

確認 prompt 成功回應
```
$ curl http://localhost:11434/api/generate \
  -d '{
    "model": "minimax-m2.5",
    "prompt": "Hello! Can you give me a quick summary of what minimax is?"
  }'
{"error":"model 'minimax-m2.5' not found"}

$ curl http://localhost:11434/api/generate \
  -d '{
    "model": "minimax-m2.5:cloud",
    "prompt": "Hello! Can you give me a quick summary of what minimax is?"
  }'
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:49.106945424Z","response":"","thinking":"The user","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:49.558857859Z","response":"","thinking":" is asking about \"minimax\" - this could refer to a few different things:\n\n1. **Minimax (","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:49.572735223Z","response":"","thinking":"company)** - A Chinese AI company that developed the abab model series\n2. **Minimax algorithm** - A","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:49.620034768Z","response":"","thinking":" decision-making algorithm used in game theory and AI\n3. **Minimax (software/tool)** - Could refer to various","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:50.084098049Z","response":"","thinking":" software products\n\nGiven that this is the context of chatting with MiniMax (the AI assistant), I should clarify what the user is","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:52.204178865Z","response":"","thinking":" asking about. Since the user might be referring to the AI assistant they're currently talking to, I should explain that Minim","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:52.930836515Z","response":"","thinking":"ax is an AI company that created me.\n\nLet me provide a helpful response that covers the main interpretations but focuses on the AI","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:53.632334721Z","response":"","thinking":" company context since that's most relevant here.","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:53.632493049Z","response":"# Minimax\n\nMinimax is an **AI","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:54.535868241Z","response":" company** based in China that specializes in developing large language models (LLMs) and AI applications. Here are the key points:\n\n## What They Do\n- **","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:55.224643515Z","response":"Founded** in 2021 by a team including former Baidu researchers\n- Developed the **abab model","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:55.870046249Z","response":" series** (abab 5, abab 5.5, etc.)\n- Focus on both research and commercial","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:56.472191131Z","response":" AI products\n\n## Products \u0026 Services\n- **MiniMax Chat** - AI chatbot","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:57.029164765Z","response":" similar to ChatGPT\n- **Kobold** - AI-powered gaming platform\n- Enterprise","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:57.622242885Z","response":" AI solutions\n- API services for developers\n\n## Key Features\n- Strong in multilingual AI capabilities\n- Focus on reasoning","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:58.145080503Z","response":" and coding abilities\n- Open-source some models (like abab 5.5)\n\n---\n\nAre you asking","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:58.682326481Z","response":" about:\n1. Minimax the AI company (which created me! 👋)\n2. The minimax algorithm (","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:59.256353676Z","response":"game theory/AI concept)\n3. Something else?\n\nLet me know and I can provide more specific details!","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:59.260522453Z","response":"","done":false}
{"model":"minimax-m2.5:cloud","remote_model":"minimax-m2.5","remote_host":"https://ollama.com:443","created_at":"2026-02-24T01:51:59.309664628Z","response":"","done":true,"done_reason":"stop","total_duration":12316299237,"prompt_eval_count":56,"eval_count":376}
```

更換 IP 設定
```
export OLLAMA_HOST=192.168.117.161:11434
```
