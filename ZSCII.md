# Tabla de conversión para probar en chrtest_z5

| Tecla | Código QL | Con el ejecutable original | Con el parcheado |
| --- | --- | --- | --- |
| a | 97 | 97 | 97 |
| A | 65 | 97 | 97 |
| á | 140 | 140 | 169 |
| é | 131 | 131 | 170 |
| í | 147 | 147 | 171 |
| ó | 150 | 150 | 172 |
| ú | 153 | 185 | 173 |
| ñ | 137 | 169 | 206 |
| ü | 135 | 135 | 157 |
| ¡ | 179 | 211 | 222 |
| ¿ | 180 | 180 | 223 |
| Ñ | 169 | 169 | 206 |
| É | 163 | 195 | 170 |

- Si con tu ejecutable nuevo `ñ` da 206 y `í` da 171, el parche funciona. Si da 169 y 147, el ejecutable no tiene el parche o no se ejecuta.
- Repite la prueba con el original (`zip_exe`) y debería salir la columna de en medio.
- Un resultado distinto de ambas columnas indicaría, por ejemplo, que el teclado no manda los códigos QL que esperamos. Pásame esos números y lo analizo.

**Prueba directa con las aventuras**

- En `faro`, `acompaña` solo existe con acento y está marcado como verbo (`c1`). Si el juego lo reconoce, te pedirá un complemento; si no, dirá que no conoce el verbo. Tampoco he podido probarlo en el juego real.
- En `aventura` está `pirámide`, un sustantivo que solo existe con acento. Una prueba útil es que el juego no responda como a una palabra desconocida.

**Por qué importa**

- En cada juego hay entre 2 y 6 palabras que solo existen con acento: `pirámide`, `peldaño`, `muñeco`, `señora`, `señorita`, `doña`, `señor`, `acompaña`, `través`.
- Sin el parche, un jugador que las escriba bien no se hace entender. Con él sí.
