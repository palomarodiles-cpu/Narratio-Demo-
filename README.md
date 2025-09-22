<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Narratio · Demo</title>

  <!-- Estilos propios (opcional: sustituye por los tuyos) -->
  <style>
    :root{--wine:#8B1A1A;--bg:#0f0f10;--text:#eaeaea;--muted:#b3b3b3}
    html,body{height:100%}
    body{margin:0;background:#0b0b0c;color:var(--text);font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue',Arial}
    .wrap{max-width:1040px;margin:0 auto;padding:40px 16px}
    .tabs{display:flex;gap:8px;margin:16px 0 24px}
    .btn{padding:8px 12px;border-radius:12px;border:1px solid #272729;background:#1c1c1d;color:#eaeaea}
    .btn--active{background:var(--wine);border-color:transparent}
    .muted{color:var(--muted)}
  </style>

  <!-- React UMD + Babel Standalone (solo para demo) -->
  <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
</head>
<body>
  <div id="root"></div>

  <!-- Tu JSX aquí: -->
  <script type="text/babel">
    const { useState, useEffect } = React;

    function App(){
      const [tab, setTab] = useState("pulse");
      useEffect(() => {
        document.title = "Narratio · Demo";
        const root = document.documentElement;
        root.style.setProperty("--wine", "#8B1A1A");
      }, []);

      return (
        <div className="wrap">
          <h1>Narratio</h1>
          <p className="muted">Storytelling verificado para Innovation Pulse</p>

          <div className="tabs">
            <button onClick={()=>setTab("pulse")} className={"btn " + (tab==="pulse" ? "btn--active" : "")}>Innovation Pulse</button>
            <button onClick={()=>setTab("traz")}  className={"btn " + (tab==="traz"  ? "btn--active" : "")}>Trazabilidad</button>
            <button onClick={()=>setTab("score")} className={"btn " + (tab==="score" ? "btn--active" : "")}>Evaluation & Scoring</button>
            <button onClick={()=>setTab("api")}   className={"btn " + (tab==="api"   ? "btn--active" : "")}>API</button>
          </div>

          {tab === "pulse" && <p>Doble scoring integrado: Trust Score (API Narratio) + Engagement Score (comportamiento real en boletines).</p>}
          {tab === "traz"  && <p>Grafo de evidencias, fuentes y auditorías con trazabilidad completa.</p>}
          {tab === "score" && <p>Trust Score en tiempo real + señales de interacción para priorización.</p>}
          {tab === "api"   && (
            <pre style={{background:"#0c0c0d", padding:"16px", borderRadius:"12px", overflow:"auto"}}>
{`POST /verify
Authorization: Bearer <token>
Content-Type: application/json

{"input": "Texto o URL a verificar", "options": {"language": "es"}}`}
            </pre>
          )}

          <p className="muted">© 2025 Narratio — Demo interna.</p>
        </div>
      );
    }

    const root = ReactDOM.createRoot(document.getElementById("root"));
    root.render(<App />);
  </script>
</body>
</html>
