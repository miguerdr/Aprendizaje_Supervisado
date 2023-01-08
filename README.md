# Aprendizaje_Supervisado
## Introdución 
Los clientes de Beta Bank se están yendo, cada mes, poco a poco. Los banqueros descubrieron que es más barato salvar a los clientes existentes que atraer nuevos. Necesitamos predecir si un cliente dejará el banco pronto. Tenemos los datos sobre el comportamiento pasado de los clientes y la terminación de contratos con el banco.

Utilizaremos técnicas de codificación para transformar características categóricas en númericas. Para evitar que las características númericas tengan diferentes escalas, utilizaremos una técnica para el escalado y estandarización de los datos. Después utilizaremos métricas para ver las proporciones de respuestas positivas y negativas. Si existe un desbalanceo fuerte utilizaremos técnicas de sobremuestreo o submuetreo con diferentes algoritmos como árbol de decisión, bosque aleatorio y regresión logística.

**Objetivo**

Crear un modelo con el máximo valor F1 posible. El valor F1 debe ser de al menos 0.59. Verificar F1 para el conjunto de prueba. Además, se debe medir la métrica AUC-ROC y compararla con el valor F1.

**Descripción de los datos**

El conjunto de datos contiene los siguientes datos:

- RowNumber: índice de cadena de datos
- CustomerId: identificador de cliente único
- Surname: apellido
- CreditScore: valor de crédito
- Geography: país de residencia
- Gender: sexo
- Age: edad
- Tenure: período durante el cual ha madurado el depósito a plazo fijo de un cliente (años)
- Balance: saldo de la cuenta
- NumOfProducts: número de productos bancarios utilizados por el cliente
- HasCrCard: el cliente tiene una tarjeta de crédito (1 - sí; 0 - no)
- IsActiveMember: actividad del cliente (1 - sí; 0 - no)
- EstimatedSalary: salario estimado

## conclusiones

- En la columna de Tenure, hay valores ausentes, estos valores los sustituiremos por la mediana
- Las columnas RowNumber, CustomerId, Surname, no son relevantes y no aportan informacion para el modelo, en este caso las eliminaremos para que nuestro modelo trabaje mejor
- Podemos observar que las columnas Gender y Geography hay que transformarlas características categóricas en numéricas
- El 20% representa la clase minotaria de la muestra Entrenamos el modelosin equilibrio de clases
- La exactitud del árbol de decisión es casi la misma que la del modelo constante. Hay un fuerte desequilibrio de clases en nuestros datos.
- Nuestro modelo tiene mayor numero de respuestas VN, 216 fallos frente a 202 aciertos
- Un recall de 0.48 y una precision de 0.48, esto es por que el numero de fallos y aciertos es muy parecido
- el valor F1 es la media armonica de recall y precision, que no es muy bajo, pero no es el objetivo Mejorar la calidad del modelo
- Utilizaremos un parámetro adicional en el modelo de Regresión logística en donde indicamos weight = “balanced” y con esto el algoritmo se encargará de equilibrar a la clase minoritaria durante el entrenamiento. Modelo Decision Tree Classifier
- El mejor valor de F1 para nuestro modelo de arbol de decision es 0.59 con un max_depth de 5 Modelo Random Forest Classifier
- El mejor valor de F1 para nuestro modelo Random Forest Classifier es 0.63, n_estimators = 40, max_depth=7 Usaremos el modelo de Random Forest Classifier, ya que nos da el mejor valor de F1 Sobremuestreo
- Con un sobremuestreo el valor de F1 disminuyo a 0.619 que esta dentro de nuestro objetivo Submuestro
- El valor de F1 disminuyo a 0.47 con un modelo Random Forest Classifier con n_estimators = 20, max_depth= 10, AUC-ROC es mayor a 0.5, F1 es menor que nuestro objetivo
- El mejor modelo* El sobremuestreo con un modelo Random Forest Classifier con n_estimators = 40, max_depth= 9, aumento el valor de F1 a 0.62 con un AUC-ROC es mayor a 0.5, muy por encima del valor de 0.5 de un modelo aleatorio
- Modelo Final*
- El valor de F1 es de 0.61, que es mayor de nuestro objetivo, y el AUC-ROC es mayor que 0.5, muy por encima del valor de 0.5 de un modelo aleatorio
