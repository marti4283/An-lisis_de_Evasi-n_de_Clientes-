# Analisis de Evasion de Clientes
Análisis de Evasión de Clientes (Churn) - TelecomX

Descripción del Proyecto
Este proyecto tiene como objetivo analizar los factores que influyen en la evasión de clientes (Churn) de una empresa de telecomunicaciones, TelecomX. A través de la exploración y visualización de datos, buscamos identificar patrones y tendencias que permitan a la empresa desarrollar estrategias efectivas para la retención de clientes.

Objetivos
•	Identificar la tasa general de evasión de clientes.
•	Explorar la relación entre variables demográficas y de servicio (categóricas y numéricas) con la evasión.
•	Determinar los principales impulsores del Churn.
•	Proponer recomendaciones accionables para reducir la tasa de evasión y mejorar la retención de clientes.

Datos
El conjunto de datos utilizado proviene de un archivo JSON alojado en GitHub: https://raw.githubusercontent.com/ingridcristh/challenge2-data-science-LATAM/refs/heads/main/TelecomX_Data.json.
Contiene información detallada sobre los clientes, incluyendo:
•	Datos del cliente (género, si es Senior Citizen, si tiene pareja o dependientes, antigüedad del contrato).
•	Servicios de teléfono (servicio de teléfono, múltiples líneas).
•	Servicios de internet (tipo de internet, seguridad online, backup online, protección de dispositivo, soporte técnico, streaming de TV, streaming de películas).
•	Datos de la cuenta (tipo de contrato, facturación sin papel, método de pago, cargos mensuales, cargos totales).
•	Variable objetivo: Churn (si el cliente canceló el servicio).

Preparación de Datos
Los pasos de preparación de datos incluyeron:
1.	Carga Inicial: Los datos JSON fueron cargados y normalizados a un DataFrame de pandas para manejar su estructura anidada.
2.	Limpieza:
o	La columna account.Charges.Total se convirtió a tipo float, manejando errores para asegurar su formato numérico.
o	Se eliminaron las filas que contenían valores vacíos o inconsistentes en las columnas Churn y total_cobrado para asegurar la integridad del análisis.
3.	Renombramiento de Columnas: Las columnas fueron renombradas a un formato más descriptivo y en español para facilitar su comprensión (ej., customerID a id, customer.gender a genero, account.Charges.Monthly a valor_mensal).
4.	Traducción de Valores Categóricos: Se tradujeron los valores de diversas columnas categóricas (ej., Churn: 'Yes' a 'Sí'; customer.gender: 'Female' a 'Femenino'; account.Contract: 'Month-to-month' a 'Mensual').
5.	Ingeniería de Características: Se creó una nueva columna Cuentas_diarias (cargos diarios) dividiendo el valor_mensal entre 30.

Análisis Exploratorio de Datos (EDA)
Se realizaron análisis descriptivos y visualizaciones para entender la distribución del Churn en relación con las diferentes variables.
Hallazgos Clave:
•	Distribución General de la Evasión: Aproximadamente el 26.6% de los clientes evaden el servicio, lo cual representa una tasa considerable que impacta los ingresos de la empresa.
•	Variables Categóricas:
o	Género: No se encontró una diferencia significativa en la tasa de Churn entre hombres y mujeres.
o	Tipo de Contrato: Los clientes con contratos mensuales muestran una tasa de Churn drásticamente más alta en comparación con los contratos anuales o bienales.
o	Servicio de Internet: Los usuarios de Fibra Óptica presentan una tasa de Churn notablemente superior a otros tipos de servicio de internet.
o	Método de Pago: El 'Cheque electrónico' está asociado con la mayor tasa de Churn.
o	Senior Citizen: Los clientes Senior (tiene +60) tienen una tasa de evasión ligeramente mayor.
•	Variables Numéricas:
o	Tiempo de Contrato (tiempo_contrato): La evasión es significativamente mayor en clientes con menor antigüedad (especialmente en los primeros meses), disminuyendo a medida que aumenta el tiempo de contrato.
o	Valor Mensual (valor_mensal): Clientes con cargos mensuales más altos (superiores a $70-$80) tienden a tener una mayor probabilidad de Churn.
o	Total Cobrado (total_cobrado): Existe una correlación entre valores totales cobrados bajos y una mayor evasión, alineado con la menor antigüedad del contrato.

Conclusiones
Los principales impulsores de la evasión de clientes son:
•	Falta de Lealtad Inicial: Los primeros meses de servicio son críticos para la retención.
•	Flexibilidad y Compromiso: Los contratos mensuales, aunque flexibles, conllevan una mayor tasa de abandono.
•	Percepción del Valor/Costo: Clientes con altos cargos mensuales son más propensos a evadir si no perciben un valor adecuado.
•	Experiencia con Servicios Específicos: El servicio de fibra óptica, a pesar de su tecnología, muestra problemas de retención.
•	Métodos de Pago: El uso de 'Cheque electrónico' se asocia con menor compromiso.

Recomendaciones Accionables
Para reducir la tasa de Churn, se proponen las siguientes estrategias:
1.	Programas de Fidelización para Clientes Nuevos: Implementar beneficios y acompañamiento en los primeros 3-6 meses para fomentar la lealtad.
2.	Incentivos para Contratos a Largo Plazo: Ofrecer descuentos o servicios premium para fomentar contratos anuales o bienales.
3.	Evaluación y Optimización de Precios: Analizar competitivamente los precios, especialmente en servicios de alto costo, y crear paquetes de valor.
4.	Mejora del Servicio de Fibra Óptica: Investigar las causas de la alta rotación (calidad, soporte, expectativas) y resolverlas.
5.	Promoción de Métodos de Pago Automatizados: Incentivar la adopción de tarjetas de crédito o transferencias bancarias automáticas.
6.	Estrategias Específicas para Clientes Senior: Diseñar programas de atención y soporte adaptados a sus necesidades.
7.	Monitoreo Proactivo de la Satisfacción: Implementar encuestas y sistemas de alerta temprana para identificar y actuar sobre clientes en riesgo.

