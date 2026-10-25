# new-ia
Mi asistente de inteligencia artificial
<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>New ia — Tu asistente</title>
<style>
:root{--bg:#0b0b12;--panel:#13131f;--panel2:#1c1b2a;--text:#f6f4ff;--muted:#a5a2ba;--purple:#8b5cf6;--purple2:#6d28d9;--border:#29283b}
*{box-sizing:border-box}body{margin:0;background:var(--bg);color:var(--text);font:15px/1.5 Inter,system-ui,-apple-system,Segoe UI,sans-serif;height:100vh}
.app{display:grid;grid-template-columns:265px 1fr;height:100vh}.sidebar{background:#0e0e17;border-right:1px solid var(--border);padding:20px;display:flex;flex-direction:column;gap:18px}
.brand{display:flex;align-items:center;gap:11px;font-weight:800;font-size:21px;letter-spacing:-.5px}.logo{width:39px;height:39px;border-radius:13px;background:linear-gradient(135deg,#a78bfa,#6d28d9);display:grid;place-items:center;font-size:21px;box-shadow:0 5px 24px #7c3aed33}
button{font:inherit;cursor:pointer;border:0;color:inherit}.newchat{background:var(--panel2);border:1px solid var(--border);padding:11px 13px;border-radius:12px;text-align:left}.newchat:hover,.suggestion:hover{border-color:#7660b9;background:#211d35}
.side-label{font-size:11px;text-transform:uppercase;letter-spacing:1.2px;color:var(--muted);margin:8px 0 0}.history{display:flex;flex-direction:column;gap:5px}.history button{background:transparent;text-align:left;padding:9px 10px;border-radius:9px;color:#d6d2e7;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}.history button:hover{background:var(--panel2)}.side-bottom{margin-top:auto;color:var(--muted);font-size:12px}
.main{display:flex;flex-direction:column;min-width:0}.topbar{height:65px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;padding:0 25px}.model{color:#d8d2ed;font-weight:600}.status{font-size:12px;color:#c4b5fd;background:#251b3d;padding:6px 10px;border-radius:99px}
.conversation{flex:1;overflow:auto;padding:34px 20px 20px}.content{max-width:800px;margin:0 auto}.welcome{text-align:center;padding:8vh 0 25px}.biglogo{margin:0 auto 20px;width:66px;height:66px;border-radius:22px;display:grid;place-items:center;background:linear-gradient(135deg,#a78bfa,#6d28d9);font-size:32px;box-shadow:0 10px 45px #7c3aed33}.welcome h1{font-size:clamp(28px,4vw,40px);letter-spacing:-1.5px;margin:0 0 10px}.welcome p{color:var(--muted);margin:0 auto 28px;max-width:470px}.suggestions{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px;max-width:650px;margin:auto}.suggestion{background:var(--panel);border:1px solid var(--border);padding:15px;border-radius:14px;text-align:left;color:#e9e5f7}.suggestion span{display:block;color:var(--muted);font-size:12px;margin-top:4px}
.message{display:flex;gap:12px;margin:20px 0;align-items:flex-start}.avatar{flex:0 0 32px;width:32px;height:32px;border-radius:11px;display:grid;place-items:center;background:#29213e}.message.user .avatar{background:#29283b}.bubble{max-width:100%;white-space:pre-wrap;overflow-wrap:anywhere;padding:4px 0}.message.assistant .bubble{color:#e8e4f4}.message.user .bubble{background:var(--panel2);border:1px solid var(--border);padding:11px 14px;border-radius:15px}.label{font-size:12px;color:var(--muted);margin-bottom:4px}
.composer-wrap{padding:10px 20px 22px}.composer{max-width:800px;margin:auto;border:1px solid #39364e;background:var(--panel);border-radius:19px;padding:12px 13px 9px;box-shadow:0 10px 35px #0003}.composer textarea{width:100%;resize:none;min-height:46px;max-height:160px;border:0;outline:0;background:transparent;color:var(--text);font:inherit;padding:8px}.composer textarea::placeholder{color:#85819d}.tools{display:flex;align-items:center;gap:7px}.tool{background:transparent;color:var(--muted);padding:7px 9px;border-radius:9px;font-size:12px}.tool:hover{background:var(--panel2);color:white}.send{margin-left:auto;background:var(--purple);color:white;width:37px;height:37px;border-radius:12px;font-size:19px}.send:hover{background:var(--purple2)}.disclaimer{text-align:center;color:#77738b;font-size:11px;margin:10px auto 0;max-width:800px}.notice{border:1px solid #4a3b70;background:#1c1630;color:#d8cbff;border-radius:12px;padding:12px 14px;font-size:13px;margin-top:16px}
@media(max-width:720px){.app{grid-template-columns:1fr}.sidebar{display:none}.topbar{padding:0 16px}.conversation{padding:20px 15px}.welcome{padding-top:6vh}.suggestions{grid-template-columns:1fr}.composer-wrap{padding:8px 12px 14px}.topbar .status{font-size:10px}}
</style>
</head>
<body>
<div class="app">
<aside class="sidebar">
  <div class="brand"><div class="logo">✦</div>New ia</div>
  <button class="newchat" id="newChat">＋ &nbsp; Nuevo chat</button>
  <div class="side-label">Tus conversaciones</div>
  <div class="history" id="history"><button>Tu primera conversación</button></div>
  <div class="side-bottom">New ia · Asistente configurable<br>Conecta un servidor de IA desde Ajustes.</div>
</aside>
<main class="main">
  <header class="topbar"><div class="model">New ia <span style="color:#918ba8;font-weight:400">· Asistente</span></div><div class="status" id="status">✦ Modo demo</div></header>
  <section class="conversation" id="conversation"><div class="content" id="content">
    <div class="welcome" id="welcome"><div class="biglogo">✦</div><h1>¿Qué hacemos hoy?</h1><p>Soy New ia, tu espacio para aprender, crear y resolver ideas en español.</p>
      <div class="suggestions">
        <button class="suggestion" data-prompt="Explícame un tema difícil de forma sencilla">💡 Aprender algo nuevo<span>Explicaciones paso a paso</span></button>
        <button class="suggestion" data-prompt="Ayúdame a escribir código y explícame cómo funciona">⌘ Escribir código<span>Crear y entender programas</span></button>
        <button class="suggestion" data-prompt="Dame ideas creativas para un proyecto">✧ Inspiración creativa<span>Ideas para empezar</span></button>
        <button class="suggestion" data-prompt="Ayúdame a investigar un tema y dime qué fuentes debería consultar">◎ Investigar un tema<span>Plan de búsqueda y fuentes</span></button>
      </div>
      <div class="notice">Modo demo: conecta tu propio servidor de IA en ⚙ Ajustes para activar respuestas reales. No pongas claves API en esta página pública.</div>
    </div>
  </div></section>
  <div class="composer-wrap"><div class="composer"><textarea id="prompt" rows="1" placeholder="Escribe tu mensaje a New ia..."></textarea><div class="tools"><button class="tool" id="voice">🎙 Voz</button><button class="tool" id="web">◎ Buscar en internet</button><button class="tool" id="image">▧ Crear imagen</button><button class="tool" id="settings">⚙ Ajustes</button><button class="send" id="send" aria-label="Enviar">↑</button></div></div><div class="disclaimer">Revisa la información importante. No introduzcas contraseñas ni datos privados.</div></div>
</main>
</div>
<script>
const promptBox=document.getElementById('prompt'), content=document.getElementById('content'), conversation=document.getElementById('conversation');
let welcome=document.getElementById('welcome'), webMode=false, imageMode=false, busy=false;
const statusEl=document.getElementById('status');
let endpoint=localStorage.getItem('newia_endpoint')||'';
function scrollBottom(){conversation.scrollTop=conversation.scrollHeight}
function addMessage(role,text){if(welcome){welcome.remove();welcome=null;}const row=document.createElement('div');row.className='message '+role;const av=document.createElement('div');av.className='avatar';av.textContent=role==='user'?'T':'✦';const body=document.createElement('div');body.style.minWidth='0';const label=document.createElement('div');label.className='label';label.textContent=role==='user'?'Tú':'New ia';const bubble=document.createElement('div');bubble.className='bubble';bubble.textContent=text;body.append(label,bubble);row.append(av,body);content.append(row);scrollBottom();return bubble}
function showWelcome(){content.innerHTML='';const w=document.createElement('div');w.className='welcome';w.innerHTML='<div class="biglogo">✦</div><h1>¿Qué hacemos hoy?</h1><p>Soy New ia, un asistente configurable para aprender, crear y resolver ideas.</p><div class="suggestions"><button class="suggestion" data-prompt="Explícame un tema difícil paso a paso">💡 Aprender<span>Explicaciones claras</span></button><button class="suggestion" data-prompt="Ayúdame a crear una aplicación y explica el código">⌘ Programar<span>Crear y depurar código</span></button><button class="suggestion" data-prompt="Dame ideas creativas para un proyecto">✧ Crear<span>Ideas y planificación</span></button><button class="suggestion" data-prompt="Ayúdame a investigar este tema y sugiere fuentes fiables">◎ Investigar<span>Organizar una búsqueda</span></button></div><div class="notice">Para usar un modelo real, configura un endpoint de backend en ⚙ Ajustes. La página por sí sola no incluye un modelo ni claves de acceso.</div>';content.append(w);welcome=w;w.querySelectorAll('[data-prompt]').forEach(b=>b.addEventListener('click',()=>{promptBox.value=b.dataset.prompt;promptBox.focus()}))}
async function send(text){text=(text??promptBox.value).trim();if(!text||busy)return;addMessage('user',text);promptBox.value='';promptBox.style.height='auto';const mode=imageMode?'image':webMode?'web':'chat';webMode=false;imageMode=false;document.getElementById('web').style.color='';document.getElementById('image').style.color='';promptBox.placeholder='Escribe tu mensaje a New ia...';busy=true;document.getElementById('send').disabled=true;const bubble=addMessage('assistant','Pensando…');
try{
 if(!endpoint){bubble.textContent='New ia está en modo demo: todavía no hay un modelo conectado. Abre ⚙ Ajustes y añade la URL de tu backend de IA. Por seguridad, la clave API debe permanecer en el servidor, nunca en este archivo HTML.';return;}
 const res=await fetch(endpoint,{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({message:text,mode,history:[...content.querySelectorAll('.message')].slice(-12).map(m=>({role:m.classList.contains('user')?'user':'assistant',content:m.querySelector('.bubble')?.textContent||''}))})});
 if(!res.ok)throw new Error('El servidor respondió con HTTP '+res.status);
 const data=await res.json();const answer=data.reply??data.message??data.output_text??data.choices?.[0]?.message?.content;
 if(typeof answer!=='string')throw new Error('Formato de respuesta no reconocido. El backend debe devolver JSON con { "reply": "..." }.');
 bubble.textContent=answer;
}catch(e){bubble.textContent='No he podido conectar con el servidor de IA. Comprueba la URL, que el backend esté activo y que permita solicitudes desde esta página (CORS). Detalle: '+e.message;}
finally{busy=false;document.getElementById('send').disabled=false;scrollBottom();}
}
document.getElementById('send').addEventListener('click',()=>send());
promptBox.addEventListener('keydown',e=>{if(e.key==='Enter'&&!e.shiftKey){e.preventDefault();send()}});
promptBox.addEventListener('input',()=>{promptBox.style.height='auto';promptBox.style.height=Math.min(promptBox.scrollHeight,160)+'px'});
document.getElementById('web').addEventListener('click',()=>{webMode=!webMode;imageMode=false;document.getElementById('web').style.color=webMode?'#c4b5fd':'';document.getElementById('image').style.color='';promptBox.placeholder=webMode?'¿Qué quieres investigar?':'Escribe tu mensaje a New ia...'});
document.getElementById('image').addEventListener('click',()=>{imageMode=!imageMode;webMode=false;document.getElementById('image').style.color=imageMode?'#c4b5fd':'';document.getElementById('web').style.color='';promptBox.placeholder=imageMode?'Describe la imagen (requiere backend compatible)...':'Escribe tu mensaje a New ia...'});
document.getElementById('voice').addEventListener('click',()=>{const SR=window.SpeechRecognition||window.webkitSpeechRecognition;if(!SR){alert('El dictado por voz no está disponible en este navegador. Prueba con Chrome o el micrófono del teclado.');return;}const r=new SR();r.lang='es-ES';r.onresult=e=>{promptBox.value=e.results[0][0].transcript;promptBox.focus()};r.start()});
document.getElementById('newChat').addEventListener('click',()=>{showWelcome();promptBox.value='';});
document.getElementById('settings').addEventListener('click',()=>{const value=prompt('URL del endpoint de tu backend de IA (POST JSON). Debe devolver JSON con una propiedad "reply". Déjalo vacío para usar el modo demo. No pegues aquí claves API.',endpoint);if(value===null)return;endpoint=value.trim();if(endpoint)localStorage.setItem('newia_endpoint',endpoint);else localStorage.removeItem('newia_endpoint');statusEl.textContent=endpoint?'✦ Backend configurado':'✦ Modo demo';alert(endpoint?'Endpoint guardado en este navegador. Asegúrate de que sea tu servidor de confianza y admita CORS.':'Se ha activado el modo demo.');});
statusEl.textContent=endpoint?'✦ Backend configurado':'✦ Modo demo';
</script>
</body>
</html>
