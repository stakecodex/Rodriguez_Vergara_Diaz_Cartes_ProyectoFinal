# 👓 Mundo Visión - Sistema de Gestión Óptico

![.NET](https://img.shields.io/badge/.NET-5C2D91?style=for-the-badge&logo=.net&logoColor=white)
![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white)
![Windows Forms](https://img.shields.io/badge/Windows%20Forms-0078D7?style=for-the-badge&logo=windows&logoColor=white)
![Visual Studio](https://img.shields.io/badge/Visual%20Studio-5C2D91?style=for-the-badge&logo=visual-studio&logoColor=white)

> Sistema integral de escritorio para la administración, cotización y venta de productos ópticos, desarrollado en C# con Windows Forms.

---

## 📖 Descripción del Proyecto

**Mundo Visión** es una solución de software diseñada para optimizar el flujo de trabajo de una óptica moderna. El sistema reemplaza los procesos manuales con una interfaz intuitiva y robusta, permitiendo gestionar el ciclo completo de venta: desde la cotización de una receta médica hasta la emisión de la boleta y el descuento de inventario.

El proyecto destaca por su arquitectura basada en **Programación Orientada a Objetos (POO)**, persistencia de datos en archivos planos (`.txt`) y una interfaz gráfica personalizada (UI) que moderniza los controles nativos de Windows.

## ✨ Características Principales

### 1. 📝 Cotizador Inteligente
* Cálculo automático de precios según rangos de dioptrías (Esfera/Cilindro).
* Detección automática de tipo de lente (Monofocal, Bifocal, Multifocal).
* Validación estricta de entradas numéricas (soporte formato internacional `.` y `,`).

### 2. 👥 Gestión de Clientes (CRM)
* **Validación Real de RUT:** Algoritmo Módulo 11 para verificar autenticidad.
* **Formato Automático:** Auto-formato de RUT mientras se escribe.
* Prevención de duplicados y validación de formato de correo electrónico.

### 3. 📦 Control de Inventario
* CRUD completo de productos.
* Protección contra **Stock Negativo** y precios inválidos.
* Persistencia de datos segura.

### 4. 💰 Punto de Venta (POS)
* Integración automática: Cotización -> Cliente -> Venta.
* Cálculo de totales incluyendo marcos, cristales, tratamientos extra y envío por región.
* **Generación de Boletas:** Exportación automática de tickets de venta en formato `.txt`.

### 5. 🎨 Interfaz Moderna (Custom UI)
* Implementación de clase `Estilos.cs` para unificación visual.
* Botones con bordes redondeados y efectos *hover*.
* Diseño responsivo y paleta de colores corporativa.

---

## 🛠️ Aspectos Técnicos Destacados

El código implementa prácticas de programación defensiva ("Blindaje"):

* **Manejo de Excepciones:** Uso de bloques `try-catch` en lecturas de archivos para evitar cierres inesperados por corrupción de datos.
* **Validación de Inputs:** Restricción de teclas en tiempo real (`KeyPress`) para asegurar integridad de datos (solo números en teléfonos, solo letras en nombres).
* **IDs Autoincrementales:** Lógica para generar identificadores únicos basados en el último registro existente.

```csharp
// Ejemplo de validación de RUT en tiempo real
private void FormatearRutAutomatico(object sender, EventArgs e)
{
    TextBox txt = (TextBox)sender;
    string texto = txt.Text.Replace("-", "").Replace(".", ""); 
    if (texto.Length > 1)
    {
        string cuerpo = texto.Substring(0, texto.Length - 1);
        string dv = texto.Substring(texto.Length - 1, 1);
        txt.Text = cuerpo + "-" + dv;
    }
}
