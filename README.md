# Silicio sobre Ruedas — FPGAs en Automoción e Intel–Altera (2015–2025)

Presentación interactiva en HTML (100% *offline* y sin dependencias externas) para la asignatura **Dispositivos Electrónicos Programables**, dedicada a analizar qué necesidades técnicas del sector automovilístico respecto a las FPGAs impulsaron la adquisición de **Altera por Intel ($16.700 millones, 2015)**.

## 🌐 Ver presentación online (GitHub Pages)

👉 **[Abrir presentación interactiva](https://josescobedov.github.io/Presentaci-nFPGA/)**

*(También funciona abriendo directamente `index.html` en cualquier navegador sin conexión a internet).*

---

## ✨ Características principales

- **Mapa FPGA interactivo de 11 nodos (`CLB_01`–`CLB_11`):** pantalla de inicio en arquitectura de matriz FPGA con *Switch Boxes* dinámicas y **Modo Viaje** activado por defecto.
- **Navegación 100% por clic (sin necesidad de teclado):** clic en cualquier nodo del mapa para entrar con zoom, clic sobre la diapositiva para avanzar al siguiente nodo y barra inferior táctil/clic con acceso al mapa y repetición de animaciones.
- **Interactividad técnica integrada:**
  - *Diapositiva 6:* Matriz del Silicio Automotriz (MCU vs. GPU vs. FPGA vs. ASIC) con enfoque interactivo por columna.
  - *Diapositiva 7:* Esquema interactivo de la placa real **Audi zFAS** con inspección de sus 4 chips (`Altera Cyclone V SoC`, `Mobileye EyeQ3`, `NVIDIA Tegra K1` e `Infineon AURIX`).
- **Herramientas de ponente (ocultas durante la proyección):**
  - `N`: panel lateral con el guion oral sincronizado y cronómetro.
  - `S`: ventana secundaria de presentador sincronizada para proyector en pantalla extendida.
  - `Q`: banco privado de 7 preguntas difíciles y respuestas verificadas.
  - `Ctrl + P`: exportación limpia a PDF apaisado 16:9 de exactamente 11 páginas.
- **Rigor académico contrastado:** 21 referencias numeradas en la diapositiva final, incluyendo 6 artículos científicos revisados por pares de revistas universitarias (**IEEE Access**, **IEEE Trans. Intell. Veh.**, **IEEE ITS Magazine**, **IEEE Trans. ITS** y **MDPI Electronics**), fuentes primarias de Intel/Altera/TTTech/Silver Lake y estándares **ISO 26262** / **AEC-Q100**.

---

## 📂 Estructura del repositorio

```text
.
├── index.html                                         # Presentación interactiva completa (11 diapositivas + Mapa FPGA)
├── assets/
│   └── slide1_hero.png                                # Ilustración técnica de portada (arquitectura heterogénea embarcada)
├── guion_exposicion_fpgas_automocion_intel_altera.md  # Guion maestro, notas orales, banco de debate y bibliografía completa
├── .nojekyll                                          # Publicación estática directa en GitHub Pages
└── README.md
```
