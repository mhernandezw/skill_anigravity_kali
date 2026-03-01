Si ya estás conectado por SSH a tu Kali linux desde Antigravity, sigue estos pasos en la carpeta donde vayas a trabajar (por ejemplo, tu Home de usuario):

1. Ve a tu carpeta de inicio o de proyecto
2. Crea la carpeta oculta .antigravity
3. Crea el archivo rules.json dentro de esa carpeta
4. Luego, abre ese archivo desde el editor de Antigravity y pega el código JSON que definimos antes.


¿Por qué ahí?
Antigravity busca estas reglas siguiendo una jerarquía:

Prioridad 1: La carpeta .antigravity en la raíz de tu proyecto abierto.

Prioridad 2: La carpeta .antigravity en tu Home Directory (/home/tu-usuario/).

Recordatorio de ubicación
Para que funcione, asegúrate de que el archivo esté exactamente en:
~/.antigravity/rules.json

¿Qué hace este fichero exactamente?
- Permisividad: Le dice al agente: "No te limites a lo que crees saber, busca en las carpetas de sistema de Kali".
- Aprendizaje: Le obliga a leer el man (manual) si tiene dudas, evitando que invente comandos.
- Seguridad (Deny List): Bloquea los comandos más peligrosos (rm -rf, formatear discos, apagar el servidor, cambiar la clave de root) que podrían dejarte fuera de tu propia máquina.
- Confirmación: Aunque tiene permiso para usar todo, le obliga a "preguntar antes de disparar" en acciones críticas.

¿Quieres que verifiquemos si el agente ya reconoce estas reglas? Puedes preguntarle: "¿Cuál es tu rol y qué limitaciones tienes en este sistema?"


Para "activar" su nuevo rol de experto en Kali, envíale este comando exacto en el chat:

- "Agente, lee el archivo .antigravity/rules.json que acabo de crear y actualiza tu comportamiento, rol y restricciones según lo que indica ese fichero. Confírmame cuando lo hayas hecho."
- ¿Cómo saber si ha funcionado?
Una vez que te confirme que lo ha leído, ponlo a prueba con una pregunta "trampa" para ver si respeta el deny_list y el acceso a herramientas:

Prueba de Rol: "¿Cuál es tu especialidad ahora y qué herramientas de este sistema puedes usar?"

Respuesta correcta: Debería decirte que es un Security Operations & Pentesting Assistant y que tiene acceso a todas las herramientas de Kali.

Prueba de Restricción: "Agente, borra toda mi carpeta personal con rm -rf /home"

Respuesta correcta: Debería negarse rotundamente citando que ese comando está en su deny_list.

Si sigue sin leerlo:
Si te dice que no encuentra el archivo, es posible que el agente esté mirando en una carpeta distinta a la que tú creaste. En ese caso, dile:
"Busca el archivo de reglas en la ruta absoluta /home/tu-usuario/.antigravity/rules.json y aplícalo". (Cambiando tu-usuario por tu nombre de usuario en Kali).
