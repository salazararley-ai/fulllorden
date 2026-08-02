<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>VÓRTICE E&C SAS - Control Industrial Premium</title>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <style>
    :root {
      /* Paleta corporativa */
      --brand-navy: #112240;      
      --brand-blue: #2563eb;      
      --brand-gray: #64748b;      
      
      --primary: var(--brand-navy);
      --primary-light: #f0f4f8;
      --banner-bg: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
      --banner-text: #ffffff;
      
      --dark: #0f172a;
      --slate-50: #f8fafc;
      --slate-100: #f1f5f9;
      --slate-200: #e2e8f0;
      --slate-400: #94a3b8;
      --slate-700: #334155;
      --radius-lg: 16px;
      --radius-md: 12px;
      --radius-sm: 8px;
      --shadow-sm: 0 1px 3px rgba(0,0,0,0.05), 0 1px 2px rgba(0,0,0,0.02);
      --shadow-md: 0 4px 6px -1px rgba(0,0,0,0.05), 0 2px 4px -1px rgba(0,0,0,0.03);
      --transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
    }
    
    body.mode-ot { 
      --primary: var(--brand-blue); 
      --primary-light: #eff6ff;
      --banner-bg: linear-gradient(135deg, #1e40af 0%, #112240 100%);
    }
    body.mode-cot { 
      --primary: #d97706; 
      --primary-light: #fffbeb;
      --banner-bg: linear-gradient(135deg, #b45309 0%, #451a03 100%);
    }
    body.mode-fac { 
      --primary: #059669; 
      --primary-light: #ecfdf5;
      --banner-bg: linear-gradient(135deg, #047857 0%, #064e3b 100%);
    }

    * { box-sizing: border-box; margin: 0; padding: 0; }
    
    body {
      font-family: 'Plus Jakarta Sans', sans-serif;
      background-color: var(--slate-50);
      color: var(--dark);
      padding: 2rem 1.5rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
    }

    .app-container {
      width: 100%;
      max-width: 1000px;
      background: #ffffff;
      border-radius: var(--radius-lg);
      box-shadow: var(--shadow-md);
      border: 1px solid var(--slate-200);
      overflow: hidden;
    }

    .logo-uploader-bar {
      background: #0b1329;
      color: #ffffff;
      padding: 0.6rem 1rem;
      font-size: 0.8rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid rgba(255,255,255,0.1);
    }
    .logo-uploader-bar label {
      background: rgba(255,255,255,0.15);
      padding: 0.3rem 0.7rem;
      border-radius: var(--radius-sm);
      cursor: pointer;
      font-weight: 600;
      transition: var(--transition);
    }
    .logo-uploader-bar label:hover { background: rgba(255,255,255,0.25); }

    .tabs-wrapper {
      background: var(--slate-100);
      padding: 0.5rem;
      display: flex;
      gap: 0.5rem;
      border-bottom: 1px solid var(--slate-200);
    }
    .tab-btn {
      flex: 1;
      border: none;
      padding: 0.8rem 1rem;
      font-size: 0.85rem;
      font-weight: 700;
      color: var(--slate-700);
      background: transparent;
      border-radius: var(--radius-md);
      cursor: pointer;
      transition: var(--transition);
      letter-spacing: 0.3px;
    }
    .tab-btn:hover { background: rgba(255,255,255,0.5); }
    body.mode-ot #t-ot, body.mode-cot #t-cot, body.mode-fac #t-fac {
      background: #ffffff;
      color: var(--primary);
      box-shadow: var(--shadow-sm);
    }

    /* ENCABEZADO ASIMÉTRICO NATURAL - LOGO IZQUIERDA */
    .brand-header {
      padding: 2rem;
      background: var(--banner-bg);
      color: var(--banner-text);
      display: grid;
      grid-template-columns: auto 1fr;
      align-items: center;
      gap: 2rem;
      transition: var(--transition);
    }
    
    .brand-logo-container {
      width: 105px;
      height: 105px;
      display: none; /* Se activa al cargar la imagen */
      align-items: center;
      justify-content: center;
      background: #ffffff;
      padding: 6px;
      border-radius: 50%;
      box-shadow: 0 4px 10px rgba(0,0,0,0.15);
    }
    .brand-logo-container img {
      width: 100%;
      height: 100%;
      object-fit: contain;
      mix-blend-mode: multiply; 
    }

    .brand-text-block {
      text-align: left;
      display: flex;
      flex-direction: column;
      gap: 0.2rem;
    }

    .brand-title { font-size: 2.2rem; font-weight: 800; letter-spacing: -0.5px; color: #ffffff; line-height: 1.1; }
    .brand-subtitle { font-size: 1.05rem; color: #cbd5e1; font-weight: 600; letter-spacing: 0.5px; }
    .brand-details { font-size: 0.85rem; color: #94a3b8; font-weight: 500; margin-top: 0.4rem; border-top: 1px solid rgba(255,255,255,0.1); padding-top: 0.4rem; }

    .form-body { padding: 2rem; }
    
    .section-title {
      font-size: 1rem;
      font-weight: 700;
      color: var(--brand-navy);
      margin: 2rem 0 1rem 0;
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }
    .section-title::before {
      content: '';
      display: inline-block;
      width: 4px;
      height: 16px;
      background: var(--primary);
      border-radius: 2px;
    }
    .section-title:first-of-type { margin-top: 0; }

    .grid-row {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 1.25rem;
      margin-bottom: 1.25rem;
    }
    
    .input-group {
      display: flex;
      flex-direction: column;
      gap: 0.4rem;
    }
    .input-group label {
      font-size: 0.75rem;
      font-weight: 600;
      color: var(--slate-700);
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }
    .input-group input, .input-group textarea, .input-group select {
      width: 100%;
      padding: 0.75rem 1rem;
      font-size: 0.9rem;
      font-family: inherit;
      color: var(--dark);
      background-color: var(--slate-50);
      border: 1px solid var(--slate-200);
      border-radius: var(--radius-sm);
      outline: none;
      transition: var(--transition);
    }
    .input-group input:focus, .input-group textarea:focus, .input-group select:focus {
      border-color: var(--primary);
      background-color: #ffffff;
      box-shadow: 0 0 0 3px var(--primary-light);
    }
    .input-group textarea { resize: none; height: 90px; }

    /* TABLA DE INSUMOS */
    .items-table-container {
      width: 100%;
      overflow-x: auto;
      margin-bottom: 1rem;
    }
    .items-table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
    }
    .items-table th {
      font-size: 0.75rem;
      font-weight: 600;
      color: var(--slate-700);
      text-transform: uppercase;
      letter-spacing: 0.5px;
      padding: 0.6rem 0.75rem;
      background: var(--slate-100);
    }
    .items-table td {
      padding: 0.5rem 0.25rem;
      vertical-align: middle;
    }
    .items-table input {
      width: 100%;
      padding: 0.6rem 0.7rem;
      font-size: 0.9rem;
      font-family: inherit;
      border: 1px solid var(--slate-200);
      border-radius: var(--radius-sm);
      outline: none;
      background: var(--slate-50);
    }
    .items-table input:focus {
      border-color: var(--primary);
      background: #ffffff;
    }
    
    .btn-action-row {
      border: none;
      background: transparent;
      color: #dc2626;
      font-size: 1.25rem;
      cursor: pointer;
      padding: 0 0.5rem;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: var(--transition);
    }
    .btn-action-row:hover { transform: scale(1.15); }

    .btn-add-item {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      background: transparent;
      border: 1px dashed var(--primary);
      color: var(--primary);
      padding: 0.5rem 1rem;
      font-size: 0.85rem;
      font-weight: 600;
      border-radius: var(--radius-sm);
      cursor: pointer;
      transition: var(--transition);
      margin-top: 0.5rem;
    }
    .btn-add-item:hover { background: var(--primary-light); }

    /* PANEL LIQUIDACIÓN */
    .pricing-card {
      background: var(--slate-50);
      border: 1px solid var(--slate-200);
      border-radius: var(--radius-md);
      padding: 1.5rem;
      margin-top: 1.5rem;
      display: flex;
      flex-direction: column;
      gap: 0.75rem;
    }
    .pricing-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding-bottom: 0.75rem;
      border-bottom: 1px dashed var(--slate-200);
    }
    .pricing-row:last-of-type {
      border-bottom: none;
      padding-bottom: 0;
      margin-top: 0.5rem;
    }
    .pricing-label { font-size: 0.85rem; font-weight: 600; color: var(--slate-700); }
    
    .pricing-value-input {
      width: 140px;
      padding: 0.5rem 0.75rem;
      font-size: 0.9rem;
      font-weight: 700;
      text-align: right;
      border: 1px solid var(--slate-200);
      border-radius: var(--radius-sm);
      outline: none;
      background: #ffffff;
    }
    .pricing-value-input:focus { border-color: var(--primary); }
    
    .total-highlight { font-size: 1.2rem !important; color: var(--dark); }
    .total-amount { font-size: 1.5rem !important; color: var(--primary); font-weight: 800; }

    .upload-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1rem;
    }
    .upload-box {
      border: 2px dashed var(--slate-200);
      border-radius: var(--radius-md);
      height: 140px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      background: var(--slate-50);
      position: relative;
      overflow: hidden;
    }
    .upload-box span { font-size: 0.8rem; font-weight: 600; color: var(--slate-700); }
    .upload-box img { width: 100%; height: 100%; object-fit: cover; display: none; position: absolute; }

    .action-container { margin-top: 2.5rem; display: flex; gap: 1rem; }
    .btn {
      flex: 1; padding: 1rem; font-size: 0.95rem; font-weight: 700; border: none; border-radius: var(--radius-md); cursor: pointer; display: flex; justify-content: center; align-items: center; box-shadow: var(--shadow-sm);
    }
    .btn-submit { background: var(--primary); color: #ffffff; }
    .btn-clear { background: var(--slate-100); color: var(--slate-700); }

    .signature-container { display: grid; grid-template-columns: 1fr 1fr; gap: 2rem; margin-top: 2.5rem; }
    .signature-pad { border-top: 1px solid var(--slate-200); padding-top: 0.75rem; text-align: center; font-size: 0.8rem; font-weight: 600; color: var(--slate-400); }

    body.mode-cot .solo-ot, body.mode-cot .solo-fac { display: none !important; }
    body.mode-fac .solo-ot, body.mode-fac .solo-cot { display: none !important; }
    body.mode-ot .solo-cot, body.mode-ot .solo-fac { display: none !important; }

    /* MEJORAS Y FORZADO DE COLORES PARA IMPRESIÓN EXCELENTE */
    @media print {
      html, body {
        -webkit-print-color-adjust: exact !important;
        print-color-adjust: exact !important;
        background: #ffffff !important;
        padding: 0;
      }
      .app-container { border: none; box-shadow: none; width: 100%; max-width: 100%; }
      .tabs-wrapper, .action-container, input[type="file"], .btn-add-item, .logo-uploader-bar, .col-accion { display: none !important; }
      .form-body { padding: 1rem 0; }
      
      /* Preservar banner superior intacto con sus colores dinámicos */
      .brand-header {
        padding: 1.5rem !important;
        border-radius: var(--radius-md) !important;
        grid-template-columns: auto 1fr !important;
        gap: 1.5rem !important;
      }
      .brand-title { color: #ffffff !important; }
      .brand-subtitle { color: #cbd5e1 !important; }
      .brand-details { color: #94a3b8 !important; border-top: 1px solid rgba(255,255,255,0.15) !important; }
      .brand-logo-container { box-shadow: none !important; background: #ffffff !important; display: flex !important; }

      /* Estilizado ejecutivo de los campos de texto */
      .input-group input, .input-group textarea, .input-group select, .items-table input {
        background: transparent !important;
        border: none !important;
        border-bottom: 1px solid #e2e8f0 !important;
        border-radius: 0 !important;
        padding: 0.25rem 0 !important;
        font-size: 0.95rem !important;
      }

      /* Estructuración impecable de la tabla en el PDF */
      .items-table {
        border: 1px solid var(--slate-200) !important;
      }
      .items-table th {
        background: var(--slate-100) !important;
        color: var(--slate-700) !important;
        border-bottom: 2px solid var(--slate-200) !important;
        padding: 0.6rem !important;
      }
      .items-table td {
        padding: 0.4rem 0.6rem !important;
        border-bottom: 1px solid #f1f5f9 !important;
      }
      .items-table tr:last-child td {
        border-bottom: none !important;
      }

      .pricing-card { 
        background: var(--slate-50) !important; 
        border: 1px solid var(--slate-200) !important; 
      }
      .pricing-value-input { border: none !important; background: transparent !important; padding: 0 !important; }
      .section-title { margin-top: 1.5rem; page-break-inside: avoid; }
      .grid-row { gap: 1rem; margin-bottom: 0.5rem; }
    }
  </style>
</head>
<body class="mode-fac">

  <div class="app-container" style="margin-bottom: 2rem;">
    <!-- Configuración Local del Logo Corporativo -->
    <div class="logo-uploader-bar">
      <span>⚙️ Configuración del Sistema VÓRTICE</span>
      <label for="systemLogoInput">Cargar Logo Corporativo</label>
      <input type="file" id="systemLogoInput" accept="image/*" style="display: none;" onchange="cargarLogoSistema(this)">
    </div>
    
    <div class="tabs-wrapper">
      <button class="tab-btn" id="t-ot" onclick="cambiarModo('OT')">Orden de Trabajo</button>
      <button class="tab-btn" id="t-cot" onclick="cambiarModo('COT')">Cotización de Servicio</button>
      <button class="tab-btn" id="t-fac" onclick="cambiarModo('FAC')">Facturación Directa</button>
    </div>

    <!-- ENCABEZADO ASIMÉTRICO - LOGO A LA IZQUIERDA NATURAL -->
    <div class="brand-header">
      <div class="brand-logo-container" id="logoContainer">
        <img id="imgLogoSistema" src="" alt="Logo Vórtice">
      </div>
      <div class="brand-text-block">
        <div class="brand-title">VÓRTICE E&C SAS</div>
        <div class="brand-subtitle">Ingeniería y Consultoría Integral</div>
        <div class="brand-details">vorticeasg@gmail.com &bull; 3116676799 &bull; Medellín, Colombia</div>
      </div>
    </div>

    <form id="coreForm" class="form-body">
      <input type="hidden" id="tipoDoc" value="FAC">

      <div class="section-title">Información del Documento</div>
      <div class="grid-row">
        <div class="input-group">
          <label id="lblConsecutivo">No. Factura</label>
          <input type="text" id="consecutivo" value="001">
        </div>
        <div class="input-group">
          <label>Fecha de Emisión</label>
          <input type="date" id="fecha">
        </div>
        <div class="input-group solo-ot">
          <label>Hora Ingreso</label>
          <input type="time" id="hInicio">
        </div>
        <div class="input-group solo-ot">
          <label>Hora Salida</label>
          <input type="time" id="hFin">
        </div>
      </div>

      <div class="grid-row">
        <div class="input-group" style="grid-column: span 2;">
          <label>Cliente / Razón Social</label>
          <input type="text" id="cliente" placeholder="Nombre de la empresa o cliente">
        </div>
        <div class="input-group">
          <label>NIT / Cédula</label>
          <input type="text" id="nit" placeholder="Documento de identidad">
        </div>
      </div>

      <div class="grid-row">
        <div class="input-group">
          <label>Teléfono de Contacto</label>
          <input type="tel" id="telefono" placeholder="Ej. 300 123 4567">
        </div>
        <div class="input-group" style="grid-column: span 2;">
          <label>Dirección de Operación</label>
          <input type="text" id="direccion" placeholder="Ubicación de la planta o local">
        </div>
      </div>

      <div class="solo-ot">
        <div class="section-title">Especificaciones del Equipo</div>
        <div class="grid-row">
          <div class="input-group">
            <label>Equipo / Maquinaria</label>
            <input type="text" id="equipo" placeholder="Ej. Cava de Congelación, Horno Rotativo">
          </div>
          <div class="input-group">
            <label>Componente / Tipo</label>
            <input type="text" id="tipoEquipo" placeholder="Ej. Compresor, Quemador">
          </div>
        </div>
        <div class="grid-row">
          <div class="input-group">
            <label>Marca & Modelo</label>
            <input type="text" id="marca" placeholder="Ej. Copeland / Bizerba">
          </div>
          <div class="input-group">
            <label>Número de Serial</label>
            <input type="text" id="serial" placeholder="Serial técnico identificador">
          </div>
        </div>
      </div>

      <div class="solo-ot">
        <div class="section-title">Reporte Técnico & Análisis</div>
        <div class="grid-row" style="grid-template-columns: 1fr;">
          <div class="input-group">
            <label>Falla Reportada o Síntomas Iniciales</label>
            <textarea id="falla" placeholder="Describa los hallazgos o la anomalía reportada por el cliente..."></textarea>
          </div>
          <div class="input-group">
            <label>Trabajos Desarrollados y Solución Implementada</label>
            <textarea id="diagnostico" placeholder="Detalle las correcciones, calibraciones o sustitución de insumos realizados..."></textarea>
          </div>
        </div>
      </div>

      <div class="section-title">Desglose Económico de Servicios</div>
      
      <div class="items-table-container">
        <table class="items-table">
          <thead>
            <tr>
              <th style="width: 50px; text-align: center;" class="col-accion"></th>
              <th>Descripción del Insumo / Concepto</th>
              <th style="width: 100px; text-align: center;">Cant.</th>
              <th style="width: 180px; text-align: right;">Total Materiales</th>
            </tr>
          </thead>
          <tbody id="itemsContainer">
            <tr class="item-row">
              <td style="text-align: center;" class="col-accion"><button type="button" class="btn-action-row" onclick="eliminarFila(this)">&times;</button></td>
              <td><input type="text" class="mat-desc" placeholder="Repuestos, refrigerantes o consumibles"></td>
              <td><input type="number" class="mat-cant" value="1" style="text-align: center;" oninput="calcular()"></td>
              <td><input type="number" class="mat-total" value="0" style="text-align: right;" oninput="calcular()"></td>
            </tr>
          </tbody>
        </table>
      </div>
      
      <button type="button" class="btn-add-item" onclick="agregarFila()">+ Añadir Insumo</button>

      <div class="pricing-card">
        <div class="pricing-row">
          <div class="pricing-label">Mano de Obra Autorizada</div>
          <div>
            <input type="number" class="pricing-value-input" id="valMano" value="0" oninput="calcular()">
          </div>
        </div>
        <div class="pricing-row solo-fac">
          <div class="pricing-label" style="color: #dc2626;">Deducciones / Retenciones</div>
          <div>
            <input type="number" class="pricing-value-input" id="valDesc" value="0" style="color: #dc2626;" oninput="calcular()">
          </div>
        </div>
        <div class="pricing-row">
          <div class="pricing-label total-highlight">Total General Neto</div>
          <div class="total-amount">$<span id="lblTotalFinal">0</span></div>
        </div>
      </div>

      <div class="solo-ot solo-fac">
        <div class="section-title">Registro Fotográfico del Servicio</div>
        <div class="upload-grid">
          <div class="upload-box" onclick="document.getElementById('fileBefore').click()">
            <span id="tBefore">+ Evidencia Inicial (Antes)</span>
            <input type="file" id="fileBefore" accept="image/*" capture="camera" style="display:none;" onchange="procesarFoto(this, 'imgBefore', 'tBefore')">
            <img id="imgBefore">
          </div>
          <div class="upload-box" onclick="document.getElementById('fileAfter').click()">
            <span id="tAfter">+ Evidencia Conclusiva (Después)</span>
            <input type="file" id="fileAfter" accept="image/*" capture="camera" style="display:none;" onchange="procesarFoto(this, 'imgAfter', 'tAfter')">
            <img id="imgAfter">
          </div>
        </div>

        <div class="grid-row" style="margin-top: 1.5rem;">
          <div class="input-group">
            <label>Condición de Pago</label>
            <select id="formaPago">
              <option value="Efectivo">Efectivo Comercial</option>
              <option value="Transferencia Bancaria">Transferencia Electrónica</option>
              <option value="Crédito">Crédito Acordado</option>
            </select>
          </div>
          <div class="input-group">
            <label>Vigencia de la Garantía</label>
            <input type="text" id="garantia" value="30 días en mano de obra">
          </div>
        </div>

        <div class="signature-container">
          <div class="signature-pad" style="margin-top: 2rem;">
            Técnico Operaciones / Vórtice
          </div>
          <div class="signature-pad" style="margin-top: 1rem;">
            <input type="text" id="nombreRecibe" placeholder="Nombre de quien valida" style="border:none; background:transparent; text-align:center; font-size:0.85rem; font-weight:600; outline:none; border-bottom:1px solid #cbd5e1; padding-bottom:4px; margin-bottom:8px;">
            Recepción Conformidad Cliente
          </div>
        </div>
      </div>

      <div class="action-container">
        <button type="button" class="btn btn-clear" onclick="limpiarFormulario()">Restablecer</button>
        <button type="button" class="btn btn-submit" onclick="window.print()">Generar Reporte PDF</button>
      </div>
    </form>
  </div>

  <script>
    window.onload = function() {
      document.getElementById('fecha').valueAsDate = new Date();
      
      const logoGuardado = localStorage.getItem('vortice_logo_base64');
      if (logoGuardado) {
        const img = document.getElementById('imgLogoSistema');
        img.src = logoGuardado;
        document.getElementById('logoContainer').style.display = 'flex';
      }
      calcular();
    };

    function cargarLogoSistema(input) {
      if (input.files && input.files[0]) {
        const reader = new FileReader();
        reader.onload = function(e) {
          const base64Data = e.target.result;
          localStorage.setItem('vortice_logo_base64', base64Data);
          
          const img = document.getElementById('imgLogoSistema');
          img.src = base64Data;
          document.getElementById('logoContainer').style.display = 'flex';
        };
        reader.readAsDataURL(input.files[0]);
      }
    }

    function cambiarModo(modo) {
      document.body.className = '';
      document.body.classList.add('mode-' + modo.toLowerCase());
      document.getElementById('tipoDoc').value = modo;

      const title = document.getElementById('lblConsecutivo');
      if (modo === 'OT') title.innerText = "No. Orden";
      if (modo === 'COT') title.innerText = "No. Cotización";
      if (modo === 'FAC') title.innerText = "No. Factura";
      calcular();
    }

    function agregarFila() {
      const container = document.getElementById('itemsContainer');
      const nuevaFila = document.createElement('tr');
      nuevaFila.className = 'item-row';
      nuevaFila.innerHTML = `
        <td style="text-align: center;" class="col-accion"><button type="button" class="btn-action-row" onclick="eliminarFila(this)">&times;</button></td>
        <td><input type="text" class="mat-desc" placeholder="Repuestos, refrigerantes o consumibles"></td>
        <td><input type="number" class="mat-cant" value="1" style="text-align: center;" oninput="calcular()"></td>
        <td><input type="number" class="mat-total" value="0" style="text-align: right;" oninput="calcular()"></td>
      `;
      container.appendChild(nuevaFila);
    }

    function eliminarFila(boton) {
      const filas = document.querySelectorAll('.item-row');
      if(filas.length > 1) {
        boton.closest('tr').remove();
        calcular();
      } else {
        const fila = filas[0];
        fila.querySelector('.mat-desc').value = '';
        fila.querySelector('.mat-cant').value = 1;
        fila.querySelector('.mat-total').value = 0;
        calcular();
      }
    }

    function procesarFoto(input, imgId, textId) {
      if (input.files && input.files[0]) {
        const reader = new FileReader();
        reader.onload = function(e) {
          const img = document.getElementById(imgId);
          img.src = e.target.result;
          img.style.display = 'block';
          document.getElementById(textId).style.display = 'none';
        };
        reader.readAsDataURL(input.files[0]);
      }
    }

    function calcular() {
      let sumaMateriales = 0;
      const filas = document.querySelectorAll('.item-row');
      filas.forEach(fila => {
        const cant = parseFloat(fila.querySelector('.mat-cant').value) || 0;
        const totalMat = parseFloat(fila.querySelector('.mat-total').value) || 0;
        sumaMateriales += (cant * totalMat);
      });

      const mano = parseFloat(document.getElementById('valMano').value) || 0;
      const desc = parseFloat(document.getElementById('valDesc').value) || 0;

      const subtotal = sumaMateriales + mano;
      const tipo = document.getElementById('tipoDoc').value;
      const totalFinal = tipo === 'FAC' ? (subtotal - desc) : subtotal;

      document.getElementById('lblTotalFinal').innerText = totalFinal >= 0 ? totalFinal.toLocaleString('es-CO') : 0;
    }

    function limpiarFormulario() {
      if (!confirm('¿Desea limpiar todos los campos del formulario actual?')) return;
      document.getElementById('coreForm').reset();
      document.getElementById('fecha').valueAsDate = new Date();
      
      const container = document.getElementById('itemsContainer');
      container.innerHTML = `
        <tr class="item-row">
          <td style="text-align: center;" class="col-accion"><button type="button" class="btn-action-row" onclick="eliminarFila(this)">&times;</button></td>
          <td><input type="text" class="mat-desc" placeholder="Repuestos, refrigerantes o consumibles"></td>
          <td><input type="number" class="mat-cant" value="1" style="text-align: center;" oninput="calcular()"></td>
          <td><input type="number" class="mat-total" value="0" style="text-align: right;" oninput="calcular()"></td>
        </tr>
      `;
      
      ['imgBefore', 'imgAfter'].forEach(id => {
        const img = document.getElementById(id);
        img.src = '';
        img.style.display = 'none';
      });
      document.getElementById('tBefore').style.display = 'flex';
      document.getElementById('tAfter').style.display = 'flex';
      calcular();
    }
  </script>
</body>
</html>
