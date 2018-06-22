# Recurso Cobertura de Salud

* **Estándar:** [HL7 FHIR](https://www.hl7.org/fhir)
* **Versión FHIR:** Release 3 [STU3](https://www.hl7.org/fhir)
* **Tipo de recurso:** Coverage [ver especificación](https://www.hl7.org/fhir/coverage.html)
* **Jurisdicción:** Colombia [CO	urn:iso:std:iso:3166](https://www.hl7.org/fhir/valueset-jurisdiction.html)
* **Fecha:** 2018-01-01
* **Editor:** [Interoperar](http://interoperar.com)
* **Contactos:** 
	- Jaime Alberto Ramírez <jaime.ramirez@interoperar.com>
	- Mario Enrique Cortés <mario.cortes@interoperar.com>
* **Copyright:**
	- [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/legalcode) 
	- [GNU General Public License version 3](https://www.gnu.org/licenses/gpl-3.0.md) 

## Definición [^1]

El alcance de este recurso cubre la información acerca de la cobertura de seguridad social en salud y/o plan obligatorio de salud de la persona que desempeñan el rol de paciente en una situación (acto) de salud.

Los atributos del recurso están enfocados en la información de aseguramiento, necesaria para soportar procedimientos administrativos y financieros de los servicios y procedimientos asistenciales.

[Más información](https://www.hl7.org/fhir/coverage.html)


## Descripción detallada [^2]

Descripciones detalladas de los elementos en el recurso [Coverage](https://www.hl7.org/fhir/coverage-definitions.html) (cobertura).


### Coverage
* **Definición:** Nodo raiz del recurso de información de cobertura de salud del paciente.
* [**Control:**][control] 1..1
* **Sintaxis XML:**

	```
		<?xml version="1.0" encoding="UTF-8"?>
		<Coverage xmlns="http://hl7.org/fhir">
		    ...
		</Coverage>
	``` 

---

### Extension copayment-ind
* **Definición:** Extensión opcional de elemento de dato que contiene un valor booleano que indica si existe un copago (cuota moderadora).
* [**Control:**][control] 0..*
* **Extension.id:** copayment-ind.
* **Extension.url:** https://github.com/interoperar/fhir-local-extensibility/copayment-ind
* **Extension.valueBoolean:** true | false
* **Sintaxis XML:**

	```
		<extension id="copayment-ind" url="https://github.com/interoperar/fhir-local-extensibility/copayment-ind">
        	<valueBoolean value="false"/>
    	</extension>
	``` 

---

### Coverage.identifier
* **Definición:** El principal identificador de la cobertura de salud (Número de póliza, número de contrato, etc).
* [**Control:**][control] 0..*
* [**Tipo de dato:**][DataType] [Identifier][DataType_identifier]
* **Sintaxis XML:**

	```
		<identifier>
        	<value value="987654321"/>
    	</identifier>
	``` 

---

### Coverage.status
* **Definición:** El principal identificador de la cobertura de salud (Número de póliza, número de contrato, etc).
* [**Control:**][control] 0..*
* [**Tipo de dato:**][DataType] [code][DataType_code]
* [**Terminología:**][terminologies] [Financial Resource Status Codes][codesystem-fm-status] active | cancelled | draft | entered-in-error
* **Sintaxis XML:**

	```
		<status value="active"/>
	``` 

---

### Coverage.type
* **Definición:** Tipo de cobertura o tipo de usuario del sistema de salud.
* [**Control:**][control] 0..1
* [**Tipo de dato:**][DataType] [code][DataType_code]
* [**Terminología:**][terminologies] [Tipo de cobertura][coverage-type-co] 
* **Sintaxis XML:**

	```
		<type>
        	<coding>
            	<system value="https://github.com/interoperar/fhir-local-terminologies/code-systems/coverage-type-co"/>
            	<code value="POS"/>
            	<display value="Paquete Obligatorio de Servicios"/>
        	</coding>
    	</type>
	``` 

---

### Coverage.beneficiary
* **Definición:** Persona que recibe los beneficios del plan de cobertura de salud (el paciente).
* [**Control:**][control] 0..1
* [**Tipo de dato:**][DataType] [Reference][DataType_Reference] ([Patient][Resource_Patient])
* **Sintaxis XML:**

	```
		<beneficiary>
        	<reference value="Patient/patient-example-1"/>
    	</beneficiary>
	``` 

---

### Coverage.payor
* **Definición:** Responsable por pago de los servicios de salud prestados al paciente (pagador o asegurador).
* [**Control:**][control] 0..1
* [**Tipo de dato:**][DataType] [Reference][DataType_Reference] ([Organization][Resource_Organization])
* **Sintaxis XML:**

	```
		<payor>
        	<reference value="Organization/organization-example-1"/>
    	</payor>
	``` 

---

## Ejemplos de sintaxis

### Sintaxis mínima

```
	<?xml version="1.0" encoding="UTF-8"?>
	<Coverage xmlns="http://hl7.org/fhir">
	    <id value="coverage-example-1"/>
	    <extension id="copayment-ind" url="https://github.com/interoperar/fhir-local-extensibility/copayment-ind">
	        <valueBoolean value="false"/>
	    </extension>
	    <identifier>
	        <value value="987654321"/>
	    </identifier>
	    <status value="active"/>
	    <type>
	        <coding>
	            <system value="https://github.com/interoperar/fhir-local-terminologies/code-systems/coverage-type-co"/>
	            <code value="POS"/>
	            <display value="Paquete Obligatorio de Servicios"/>
	        </coding>
	    </type>
	    <beneficiary>
	        <reference value="Patient/patient-example-1"/>
	    </beneficiary>
	    <payor>
	        <reference value="Organization/organization-example-1"/>
	    </payor>
	</Coverage>
```


[^1]: [Resource Coverage - Content](https://www.hl7.org/fhir/coverage.html)

[^2]: [Resource Coverage - Detailed Descriptions](https://www.hl7.org/fhir/coverage-definitions.html)

[control]:https://www.hl7.org/fhir/conformance-rules.html#cardinality
[DataType]:https://www.hl7.org/fhir/datatypes.html
[DataType_identifier]:https://www.hl7.org/fhir/datatypes.html#Identifier
[DataType_code]:https://www.hl7.org/fhir/datatypes.html#code
[terminologies]:https://www.hl7.org/fhir/terminologies-systems.html
[codesystem-fm-status]:https://www.hl7.org/fhir/codesystem-fm-status.html
[coverage-type-co]:https://github.com/interoperar/fhir-local-terminologies/code-systems/coverage-type-co
[DataType_Reference]:https://www.hl7.org/fhir/references.html#Reference
[Resource_Patient]:https://www.hl7.org/fhir/patient.html
[Resource_Organization]:https://www.hl7.org/fhir/organization.html
