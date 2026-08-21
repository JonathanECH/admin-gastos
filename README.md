# Planificador de Gastos - Vue 3 + Vite 💰

Una aplicación web moderna, intuitiva y totalmente responsiva diseñada para administrar tu presupuesto personal y llevar un control detallado de tus gastos diarios.

🌐 **Demo en vivo:** [https://admin-gasto-vue.netlify.app/](https://admin-gasto-vue.netlify.app/)

---

## 🚀 Características Principales

- **Gestión de Presupuesto:**
  - Definición de presupuesto inicial con validación.
  - Cálculo automático e instantáneo del **Presupuesto Total**, **Disponible** y **Gastado**.
  - Indicador gráfico circular (`CircleProgress`) que muestra el porcentaje consumido del presupuesto.
  - Opción de reiniciar la aplicación borrando presupuesto y gastos guardados previa confirmación.

- **Control Completo de Gastos (CRUD):**
  - **Añadir Gasto:** Registrar nombre, cantidad y categoría.
  - **Editar Gasto:** Modificar cualquier gasto existente seleccionándolo de la lista.
  - **Eliminar Gasto:** Borrado permanente de gastos con modal de confirmación.
  - **Validaciones:** Comprobación de campos obligatorios, cantidades mayores a cero y control de saldo disponible para evitar exceder el presupuesto.

- **Filtrado por Categorías:**
  - Filtrar gastos en tiempo real por categorías específicas (Ahorro, Comida, Casa, Gastos varios, Ocio, Salud, Suscripciones).

- **Persistencia de Datos:**
  - Guardado automático en `LocalStorage`, lo que permite mantener la información al recargar o cerrar la página.

- **Experiencia de Usuario (UI/UX):**
  - Modales interactivos para el formulario de gasto y para las confirmaciones de acciones críticas.
  - Bloqueo dinámico del scroll de la página (`body.fijar`) mientras los modales están abiertos.
  - Diseño 100% responsivo adaptable a dispositivos móviles, tablets y computadoras de escritorio.

---

## 🛠️ Tecnologías Utilizadas

- **[Vue 3](https://vuejs.org/):** Framework de JavaScript utilizando la **Composition API** (`<script setup>`, `ref`, `reactive`, `computed`, `watch`, `onMounted`).
- **[Vite](https://vitejs.dev/):** Herramienta de compilación y empaquetador ultrarrápido para el desarrollo web.
- **[SASS / SCSS](https://sass-lang.com/):** Preprocesador CSS con arquitectura modular (variables, mixins para media queries y estilos globales).
- **[vue3-circle-progress](https://www.npmjs.com/package/vue3-circle-progress):** Componente para la renderización gráfica del porcentaje de presupuesto gastado.
- **JavaScript (ES6+):** Utilidades personalizadas para la generación de IDs únicos, formateo de moneda (`USD`) y formato de fechas locales.
- **LocalStorage API:** Persistencia local de datos en el navegador del cliente.
- **[pnpm](https://pnpm.io/):** Gestor de paquetes eficiente y rápido utilizado para la administración de dependencias.
- **Netlify:** Plataforma para la integración y despliegue continuo en la nube.

---

## 📁 Estructura del Proyecto

```text
admin-gastos/
├── src/
│   ├── assets/
│   │   ├── img/                  # Iconos SVG de categorías y acciones
│   │   └── scss/                 # Archivos de estilos Sass (base, mixins, variables)
│   ├── components/
│   │   ├── Alerta.vue            # Componente para alertas de validación
│   │   ├── ControlPresupuesto.vue # Panel principal del presupuesto y gráfica
│   │   ├── Filtros.vue           # Selector de filtro por categoría
│   │   ├── Gasto.vue             # Card para la visualización de un gasto
│   │   ├── Modal.vue             # Modal para crear y editar gastos
│   │   ├── ModalConfirmar.vue    # Modal personalizado de confirmación
│   │   └── Presupuesto.vue       # Formulario inicial de presupuesto
│   ├── helpers/                  # Funciones de formateo de moneda, fecha e ID
│   ├── App.vue                   # Componente principal y lógica central
│   └── main.js                   # Punto de entrada de Vue 3
├── package.json
└── README.md
```

---

## 🔧 Instalación y Ejecución Local

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/tu-usuario/admin-gastos.git
   cd admin-gastos
   ```

2. **Instalar dependencias:**
   ```bash
   pnpm install
   ```

3. **Iniciar el servidor de desarrollo:**
   ```bash
   pnpm run dev
   ```

4. **Compilar para producción:**
   ```bash
   pnpm run build
   ```

---

## 🔗 Demo en Línea

Puedes probar la versión publicada en producción ingresando a:
👉 **[https://admin-gasto-vue.netlify.app/](https://admin-gasto-vue.netlify.app/)**
