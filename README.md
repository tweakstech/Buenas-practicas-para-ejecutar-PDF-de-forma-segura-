# Buenas 📑 prácticas para ejecutar 🔒 PDF de forma segura 💻

Los archivos **PDF** (Formato de Documento Portátil) fueron diseñados originalmente para ofrecer una forma segura y controlada de visualizar y compartir documentos, asegurando la integridad del contenido y preservando el formato en el que fue creado. Son ampliamente utilizados debido a su capacidad de mantener la estructura original del documento, sin importar el dispositivo o sistema operativo en el que se visualice.

El **PDF** está diseñado para ser un formato cerrado y controlado, lo que permite a los usuarios proteger la información mediante el uso de contraseñas, firmas digitales y otras características de seguridad. Sin embargo, este mismo nivel de control ha sido aprovechado de forma maliciosa por atacantes, que pueden insertar código dañino, como **JavaScript** o **exploit**, dentro de los archivos PDF.

Estos ataques pueden estar diseñados para **explotar vulnerabilidades** en los visores de PDF, lo que permite ejecutar código malicioso sin el conocimiento del usuario, comprometiendo su seguridad. Esto significa que, aunque el formato PDF fue creado para proteger la información, también puede ser utilizado de forma inapropiada para atacar dispositivos y robar información.

## Índice
1. [No ejecutes PDF sin saber su origen](#no-ejecutes-pdf-sin-saber-su-origen)
2. [Verifica el enlace del archivo con herramientas de análisis de seguridad](#verifica-el-enlace-del-archivo-con-herramientas-de-análisis-de-seguridad)
3. [Mantén activado ver extensiones de archivos en el sistema](#mantén-activado-ver-extensiones-de-archivos-en-el-sistema)
4. [Verifica los datos de la firma digital del archivo](#verifica-los-datos-de-la-firma-digital-del-archivo)
5. [Verifica el hash del archivo PDF](#verifica-el-hash-del-archivo-pdf)
6. [Comparte enlaces de verificación de escaneo](#comparte-enlaces-de-verificación-de-escaneo)
7. [Los PDF pueden contener instrucciones maliciosas](#los-pdf-pueden-contener-instrucciones-maliciosas)
8. [Mantén actualizado el visor de PDF que utilices](#mantén-actualizado-el-visor-de-pdf-que-utilices)
9. [Usa la conversión de PDF a imágenes para mayor seguridad](#usa-la-conversión-de-pdf-a-imágenes-para-mayor-seguridad)

## No ejecutes PDF sin saber su origen.
- Verifica siempre la fuente de los archivos PDF antes de abrirlos. Si no puedes confirmar su autenticidad, evita ejecutarlos.

## Verifica el enlace del archivo con herramientas de análisis de seguridad
- Verifica el enlace con [VirusTotal](https://www.virustotal.com) y [URLScan](https://urlscan.io) para ver si ejecuta PDF en sandbox o entornos seguros antes. Para ejecutar en un entorno seguro, puedes usar [AnyRun](https://any.run) o [VirtualBox](https://www.virtualbox.org).

## Mantén activado ver extensiones de archivos en el sistema
Es importante **ver las extensiones de los archivos** en el sistema para poder identificar correctamente el tipo de archivo con el que estás trabajando. Muchas veces, los atacantes pueden ocultar las extensiones reales de los archivos para hacerlos parecer inofensivos, como cambiar un archivo malicioso de `.exe` a `.pdf`, lo que podría engañar a los usuarios. Si tienes activada la visualización de extensiones de archivos, podrás detectar archivos sospechosos que realmente sean de otro tipo, como ejecutables disfrazados de documentos.

**Para hacerlo en Windows:**
1. Abre el **Explorador de archivos**.
2. Haz clic en la pestaña **Vista** en la parte superior.
3. Haz clic en **Opciones** (a la derecha) y selecciona **Cambiar opciones de carpeta y búsqueda**.
4. En la ventana emergente, selecciona la pestaña **Ver**.
5. Desmarca la opción **Ocultar las extensiones de archivo para tipos de archivo conocidos** y haz clic en **Aceptar**.

**Acceso rápido con comandos en Windows:**
- Puedes abrir directamente las **Opciones de carpeta** presionando `Win + R` para abrir el cuadro de ejecución, luego escribe `control folders` y presiona **Enter**.

**Usando el Registro (Regedit) para habilitar las extensiones:**
1. Abre el **Editor del Registro** presionando `Win + R`, escribe `regedit` y presiona **Enter**.
2. Navega a la siguiente clave:  
   `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced`
3. En el panel derecho, busca un valor llamado **HideFileExt**.
4. Haz doble clic en **HideFileExt** y cambia el valor a **0** (cero) para habilitar la visualización de extensiones de archivo.
5. Haz clic en **Aceptar** y reinicia el sistema si es necesario.

**Para hacerlo en macOS:**
1. Abre **Finder**.
2. Ve a **Preferencias** en el menú de Finder.
3. Marca **Mostrar todas las extensiones de archivo**.

> [!TIP]
> Asegúrate de activar la opción de ver las extensiones de archivo en tu sistema para identificar archivos sospechosos.

## Verifica los datos de la firma digital del archivo
- Los archivos PDF pueden estar firmados digitalmente para verificar su autenticidad. Para verificar la firma digital de un archivo PDF en Windows:
  1. Haz clic derecho sobre el archivo PDF y selecciona **Propiedades**.
  2. Ve a la pestaña **Firmas digitales**.
  3. Si el archivo está firmado, aparecerá una firma digital y podrás verificar si la firma es válida y si el archivo ha sido modificado desde que fue firmado.
  4. En la sección **Detalles de la firma**, puedes ver la validez de la firma y la información del firmante, como la entidad que la emitió.

**En macOS:**
1. Abre el archivo PDF con **Vista Previa**.
2. Haz clic en el botón de la firma digital en la barra de herramientas.
3. Si el archivo tiene una firma válida, podrás ver la información sobre el firmante y la validez de la firma.

> [!TIP]
> Verificar las firmas digitales ayuda a garantizar que el archivo no haya sido alterado.

## Verifica el hash del archivo PDF
- Verificar el hash de un archivo PDF es una forma eficaz de asegurarte de que el archivo no ha sido alterado o manipulado. El hash es un valor único que se genera a partir del contenido del archivo y se utiliza para identificarlo de manera precisa.

- Para verificar el hash de un archivo PDF, primero necesitas obtener el valor del hash original del archivo (por ejemplo, proporcionado por el creador del archivo o una fuente confiable). Luego, puedes generar el hash del archivo PDF descargado y compararlo con el valor original.

- Si ambos valores de hash coinciden, es seguro asumir que el archivo no ha sido modificado. Si el hash no coincide, significa que el archivo ha sido alterado y puede contener código malicioso o haber sido corrompido.

**Nota:** Los algoritmos de hash comunes incluyen **MD5**, **SHA-1** y **SHA-256**. Los valores de hash generados por estos algoritmos son únicos para cada archivo, por lo que cualquier cambio en el archivo alterará el hash.

> [!TIP]
> Usar el hash permite verificar la integridad del archivo PDF y detectar modificaciones.

## Comparte enlaces de verificación de escaneo
- Si compartes archivos, comparte los enlaces de verificación del escaneo del análisis para verificar que sea seguro.

## Los PDF pueden contener instrucciones maliciosas
- Los PDF pueden contener instrucciones por detrás para obtener privilegios ejecutando códigos como **JavaScript** o **exploit**. Al abrir el PDF, se ejecuta el código malicioso sin que te enteres.

- **Técnicas similares a las utilizadas en archivos Word y Excel:** Los archivos PDF pueden emplear técnicas maliciosas similares a las utilizadas en archivos de **Microsoft Word** y **Excel** mediante el uso de **macros**. Al igual que los macros en documentos de Word o Excel, que pueden ejecutar código malicioso sin el conocimiento del usuario, los archivos PDF pueden estar diseñados para ejecutar **scripts maliciosos**, **exploits** o **código** como **JavaScript**, que aprovechan vulnerabilidades en el software para ejecutar comandos dañinos o ejecutar exploits sin el conocimiento del usuario.

> [!WARNING]
> Los archivos PDF pueden ejecutar código malicioso sin que te des cuenta, por lo que siempre debes tener precaución al abrirlos.

## Mantén actualizado el visor de PDF que utilices
- **Recomendación:** No uses Adobe Acrobat Reader, ya que ha sido objeto de múltiples vulnerabilidades en el pasado y se ha considerado un objetivo frecuente de los atacantes. 

- Mantén siempre actualizado el visor de PDF que utilices, ya sea un lector de código abierto o uno con características de seguridad robustas.

- Asegúrate de instalar las actualizaciones de seguridad y parches cuando estén disponibles para el software que utilices, ya que muchas de estas actualizaciones abordan vulnerabilidades que podrían ser explotadas por archivos PDF maliciosos.

- Una alternativa segura es **[Foxit Reader](https://www.foxitsoftware.com/pdf-reader/)**, que cuenta con características de seguridad y actualizaciones periódicas.

> [!TIP]
> Mantén siempre actualizado el visor de PDF para prevenir vulnerabilidades de seguridad.

## Usa la conversión de PDF a imágenes para mayor seguridad
- Una forma adicional de protegerte al manejar archivos PDF potencialmente peligrosos es convertirlos a imágenes antes de abrirlos. Esta práctica elimina cualquier código potencialmente malicioso, como **JavaScript** o **exploits**, que puedan estar incrustados en el archivo PDF.

- Al convertir un PDF a una imagen (por ejemplo, a formato **PNG** o **JPEG**), solo se visualiza el contenido estático del documento, lo que significa que no se ejecutan scripts maliciosos ni comandos. Las imágenes generadas serán legítimas del formato correcto y no contendrán código ejecutable, ya que las imágenes no pueden ejecutar código de forma directa.

- Sin embargo, es importante tener en cuenta que, aunque las imágenes no pueden ejecutar código por sí solas, aún podrían emplearse técnicas similares a las de los archivos PDF maliciosos. Por ejemplo, al combinar archivos y ocultar las extensiones reales del archivo, un atacante podría intentar engañar al sistema para que el archivo de imagen sea ejecutado de forma incorrecta. Pero, al convertir un PDF a imágenes, estas técnicas no serán efectivas, ya que el archivo resultante será un archivo de imagen legítimo, sin la posibilidad de ejecutar código malicioso.

- Para convertir tus archivos PDF a imágenes de forma sencilla, puedes usar la herramienta [PDF2Go](https://www.pdf2go.com/es/pdf-a-jpg).

> [!TIP]
> Convertir PDF a imágenes elimina cualquier código malicioso, garantizando mayor seguridad.

## Nota importante: 
> [!IMPORTANT]
> Estas prácticas deben ser seguidas con seriedad, ya que actualmente se está compartiendo una gran cantidad de información en formato PDF, incluso a través de plataformas populares como **Telegram** o **cursos en línea**. Los archivos PDF pueden parecer inofensivos, pero en realidad, pueden ser utilizados para acceder a tu información sin que lo sepas. Los atacantes pueden insertar código malicioso dentro de estos archivos, y al abrirlos, pueden obtener acceso a tus datos, comprometer tu seguridad o incluso infectar tu dispositivo. Por eso es esencial ser precavido al manejar y ejecutar archivos PDF, y siempre asegurarse de que provienen de una fuente confiable.

---

## Licencia

 Este proyecto se encuentra bajo la licencia [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Consulta el archivo `LICENSE` para más detalles.

© 2024 tweakstech
