# Recurso Paciente

* **Estándar:** [HL7 FHIR](https://www.hl7.org/fhir)
* **Versión FHIR:** Release 3 [STU3](https://www.hl7.org/fhir)
* **Tipo de recurso:** Patient [ver especificación](https://www.hl7.org/fhir/patient.html)
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

El alcance de este recurso cubre la información acerca de las personas que desempeñan el rol de paciente en una situación (acto) de salud.

Los atributos del recurso están enfocados en la información demográfica y de identificación, necesaria para soportar procedimientos clínicos, administrativos, financieros y logísticos.

[Más información](https://www.hl7.org/fhir/patient.html)

## Descripción detallada [^2]

Descripciones detalladas de los elementos en el recurso [Patient](https://www.hl7.org/fhir/patient-definitions.html) (paciente).

### Patient
* **Definición:** Nodo raiz del recurso de información del paciente.
* [**Control:**][control] 1..1
* **Sintaxis XML:**

	```
		<?xml version="1.0" encoding="UTF-8"?>
		<Patient xmlns="http://hl7.org/fhir">
	    	...
		</Patient>
	``` 

---

### Patient.identifier
* **Definición:** Identificación de la persona que desempeña el rol de paciente.

	Contiene el [código de tipo de identificación](https://github.com/interoperar/fhir-local-terminologies/identifiers/personal-identifier-type-co) y el valor (número) de identificación.

* [**Control:**][control] 0..*
* [**Tipo de dato:**][DataType] [Identifier][DataType_identifier]
* **Patient.identifier.type:** ([Terminología][terminologies]) [Tipo de identificación paciente][personal-identifier-type-co] 
* **Sintaxis XML:** 
	- Sintaxis para la identificación de la persona.

	```
		<identifier id="personal">
       	<use value="official"/>
        	<type>
            	<coding>
                	<system value="https://github.com/interoperar/fhir-local-terminologies/identifiers/personal-identifier-type-co"/>
                	<code value="CC"/>
                	<display value="Cédula de Ciudadanía"/>
            	</coding>
        	</type>
        	<value value="987654321"/>
    	</identifier>
	``` 
	- Sintaxis para la identificación de la historia clínica del paciente.
	
	```
		<identifier id="clinical">
        	<use value="usual"/>
        	<value value="987654321"/>
    	</identifier>
	```

---

### Patient.active
* **Definición:** Valor que indica si el registro del paciente está activo o en uso.
* [**Control:**][control] 0..1
* [**Tipo de dato:**][DataType] [boolean][DataType_boolean] true | false
* **Sintaxis XML:**

	```
		<active value="true"/>
	``` 

---

### Patient.name
* **Definición:** Nombre de la persona que desempeña el rol de paciente.
* [**Control:**][control] 0..*
* [**Tipo de dato:**][DataType] [HumanName][DataType_HumanName]
* **Sintaxis XML:**

	```
		<name>
        	<family id="apellidos" value="Moreno Reyes"/>
        	<given id="primer-nombre" value="Mario"/>
        	<given id="segundo-nombre" value="Alfonso"/>
    	</name>
	``` 

---

### Patient.telecom
* **Definición:** Dirección de telecomunicaciones (ej: teléfono, móvil, e-mail, etc) a través del cual la persona que desempeña el rol de paciente puede ser contactada.
* [**Control:**][control] 0..*
* [**Tipo de dato:**][DataType] [ContactPoint][DataType_ContactPoint]
* **Sintaxis XML:**
	- Ejemplo de sintaxis para correo electrónico:

	```
		<telecom>
	        <system value="email"/>
	        <value value="nombre@example.com"/>
	        <use value="home"/>
    	</telecom>
	``` 
	- Ejemplo de sintaxis para teléfono móvil:

	```
		<telecom>
	        <system value="phone"/>
	        <value value="+57(300)000-0000"/>
	        <use value="mobile"/>
    	</telecom>
	``` 
	- Ejemplo de sintaxis para teléfono:

	```
		<telecom>
	        <system value="phone"/>
	        <value value="+57(1)111-1111"/>
	        <use value="home"/>
    	</telecom>
	``` 

---


### Patient.gender
* **Definición:** Género (sexo) del paciente, para fines administrativos.
* [**Control:**][control] 0..1
* [**Terminología:**][terminologies] [AdministrativeGender][codesystem-administrative-gender] male | female | other | unknown
* [**Tipo de dato:**][DataType] [code][DataType_code]
* **Sintaxis XML:**

	```
		<gender value="male"/>
	``` 

---

### Patient.birthDate
* **Definición:** Fecha de nacimiento de la persona que desempeña el rol de paciente.
* [**Control:**][control] 0..1
* [**Tipo de dato:**][DataType] [date][DataType_date]
* **Sintaxis XML:**

	```
		<birthDate value="1963-08-16"/>
	``` 

---

### Patient.deceased[x]
* **Definición:** Elemento que indica si el paciente ha fallecido o no.
* [**Control:**][control] 0..1
* [**Tipo de dato:**][DataType] [boolean][DataType_boolean] | [date][DataType_dateTime]
* **Sintaxis XML:**
	- Sintaxis de indicador booleano: true | false

	```
		<deceasedBoolean value="false"/>
	``` 
	
	- Sintaxis para fecha de defunción:

	```
		<deceasedDateTime value="2016-03-18T03:00:00"/>
	```

---

### Patient.address
* **Definición:** Dirección de la persona que desempeña el rol de paciente.
* [**Control:**][control] 0..*
* [**Tipo de dato:**][DataType] [Address][DataType_Address]
* **Sintaxis XML:**

	```
		<address>
	        <use value="home"/>
	        <type value="both"/>
	        <text value="Calle 116 # 03-27"/>
	        <city value="Bogotá D.C."/>
	        <district value="Bogotá D.C."/>
	        <postalCode value="110100"/>
	        <country value="Colombia"/>
    	</address>
    ```
    
 ---
 
### Patient.managingOrganization
* **Definición:** Organización que custodia el registro del paciente.
* [**Control:**][control] 0..1
* [**Tipo de dato:**][DataType] [	Reference][DataType_Reference] ([Organization][Resource_Organization])
* **Sintaxis XML:**

	```
		<managingOrganization>
        	<reference value="Organization/organization-example-1"/>
    	</managingOrganization>
    ```
    
 ---
 

## Ejemplos de sintaxis

### Sintaxis mínima

```
	<?xml version="1.0" encoding="UTF-8"?>
	<Patient xmlns="http://hl7.org/fhir">
	    <identifier id="personal">
	        <use value="official"/>
	        <type>
	            <coding>
	                <system value="https://github.com/interoperar/fhir-local-terminologies/identifiers/personal-identifier-type-co"/>
	                <code value="CC"/>
	                <display value="Cédula de Ciudadanía"/>
	            </coding>
	        </type>
	        <value value="987654321"/>
	    </identifier>
	    <identifier id="clinical">
	        <use value="usual"/>
	        <value value="987654321"/>
	    </identifier>
	    <active value="true"/>
	    <name>
	        <family id="family-name" value="Moreno Reyes"/>
	        <given id="given-name-1" value="Mario"/>
	        <given id="given-name-2" value="Alfonso"/>
	    </name>
	    <gender value="male"/>
	    <birthDate value="1963-08-16"/>
	</Patient>
```

### Sintaxis extendida

```
	<?xml version="1.0" encoding="UTF-8"?>
	<Patient xmlns="http://hl7.org/fhir">
	    <id value="patient-example-2"/>
	    <text>
	        <status value="generated"/>
	        <div xmlns="http://www.w3.org/1999/xhtml">
	            <h2>Moreno Reyes Mario Alfonso</h2>
	            <ul>
	                <li><b>Identificación: </b>CC 987654321</li>
	                <li><b>Historia Clínica: </b>987654321</li>
	                <li><b>Sexo: </b>Masculino</li>
	                <li><b>Fecha de nacimiento: </b>1963/Ago/16</li>
	                <li><b>Correo electrónico: </b>nombre@example.com</li>
	                <li><b>Móvil: </b>+57(300)000-0000</li>
	                <li><b>Teléfono: </b>+57(1)111-1111</li>
	                <li><b>Dirección: </b>Calle 116 # 03-27
	                    <br />Bogotá D.C.
	                    <br />110100
	                    <br />Colombia
	                </li>
	            </ul>
	        </div>
	    </text>
	    <identifier id="personal">
	        <use value="official"/>
	        <type>
	            <coding>
	                <system value="https://github.com/interoperar/fhir-local-terminologies/identifiers/personal-identifier-type-co"/>
	                <code value="CC"/>
	                <display value="Cédula de Ciudadanía"/>
	            </coding>
	        </type>
	        <value value="987654321"/>
	    </identifier>
	    <identifier id="clinical">
	        <use value="usual"/>
	        <value value="987654321"/>
	    </identifier>
	    <active value="true"/>
	    <name>
	        <family id="family-name" value="Moreno Reyes"/>
	        <given id="given-name-1" value="Mario"/>
	        <given id="given-name-2" value="Alfonso"/>
	    </name>
	    <telecom>
	        <system value="email"/>
	        <value value="nombre@example.com"/>
	        <use value="home"/>
	    </telecom>
	    <telecom>
	        <system value="phone"/>
	        <value value="+57(300)000-0000"/>
	        <use value="mobile"/>
	    </telecom>
	    <telecom>
	        <system value="phone"/>
	        <value value="+57(1)111-1111"/>
	        <use value="home"/>
	    </telecom>
	    <gender value="male"/>
	    <birthDate value="1963-08-16"/>
	    <deceasedBoolean value="false"/>
	    <address>
	        <use value="home"/>
	        <type value="both"/>
	        <text value="Calle 116 # 03-27"/>
	        <city value="Bogotá D.C."/>
	        <district value="Bogotá D.C."/>
	        <postalCode value="110100"/>
	        <country value="Colombia"/>
	    </address>
	   	 <managingOrganization>
        	<reference value="Organization/organization-example-1"/>
    	 </managingOrganization>
	</Patient>
```


[^1]: [Resource Patient - Content](https://www.hl7.org/fhir/patient.html)

[^2]: [Resource Patient - Detailed Descriptions](https://www.hl7.org/fhir/patient-definitions.html)

[control]:https://www.hl7.org/fhir/conformance-rules.html#cardinality
[DataType]:https://www.hl7.org/fhir/datatypes.html
[DataType_identifier]:https://www.hl7.org/fhir/datatypes.html#Identifier
[personal-identifier-type-co]:https://github.com/interoperar/fhir-local-terminologies/identifiers/personal-identifier-type-co
[DataType_boolean]:https://www.hl7.org/fhir/datatypes.html#boolean
[DataType_HumanName]:https://www.hl7.org/fhir/datatypes.html#HumanName
[DataType_ContactPoint]:https://www.hl7.org/fhir/datatypes.html#ContactPoint
[DataType_code]:https://www.hl7.org/fhir/datatypes.html#code
[terminologies]:https://www.hl7.org/fhir/terminologies-systems.html
[codesystem-administrative-gender]:https://www.hl7.org/fhir/codesystem-administrative-gender.html
[DataType_date]:https://www.hl7.org/fhir/datatypes.html#date
[DataType_dateTime]:https://www.hl7.org/fhir/datatypes.html#dateTime
[DataType_Address]:https://www.hl7.org/fhir/datatypes.html#Address
[DataType_Reference]:https://www.hl7.org/fhir/references.html#Reference
[Resource_Organization]:https://www.hl7.org/fhir/organization.html

