---
title: "Conversion de chaînes en types de données .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce594234e601cd8feb4723bbc383db9e3ed40522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="converting-strings-to-net-framework-data-types"></a>Conversion de chaînes en types de données .NET Framework
Si vous souhaitez convertir une chaîne en un type de données .NET Framework, utilisez la **XmlConvert** méthode répondant aux exigences de l’application. Pour obtenir la liste de toutes les méthodes de conversion disponibles dans le **XmlConvert** de classe, consultez <xref:System.Xml.XmlConvert>.  
  
 La chaîne retournée par la **ToString** méthode est une version de chaîne des données qui sont passées. En outre, il existe plusieurs types .NET Framework qui convertissent à l’aide de la **XmlConvert** classe bien qu’ils n’utilisent pas les méthodes dans les **System.Convert** classe. Le **XmlConvert** classe suit la spécification de type de données XSD (XML Schema) et possède un de données de type qui le **XmlConvert** peut mapper à.  
  
 Le tableau suivant répertorie les types de données .NET Framework et les types de chaînes retournés à l'aide du mappage de types de données XSD (XML Schema Definition). Ces types .NET Framework ne peut pas être traitées à l’aide de **System.Convert**.  
  
|Type .NET Framework|Chaîne retournée|  
|-------------------------|---------------------|  
|Boolean|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|Le format est « yyyy-MM-ddTHH:mm:sszzzzzz » et ses sous-ensembles.|  
|TimeSpan|Le format est PnYnMnTnHnMnS, c'est-à-dire que `P2Y10M15DT10H30M20S` indique une durée de 2 années, 10 mois, 15 jours, 10 heures, 30 minutes et 20 secondes.|  
  
> [!NOTE]
>  Si la conversion des types .NET Framework répertoriés dans le tableau à une chaîne à l’aide de la **ToString** (méthode), la chaîne retournée n’est pas le type de base, mais le type de chaîne XSD (XML Schema).  
  
 Le **DateTime** et **Timespan** diffère de type valeur qui un **DateTime** représente un instant, tandis qu’un **TimeSpan** représente un intervalle de temps. Le **DateTime** et **Timespan** formats sont spécifiés dans la spécification de types de données XSD (XML Schema). Exemple :  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 **Sortie**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 Le code suivant convertit un entier en chaîne :  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 **Sortie**  
  
 `<Number>200</Number>`  
  
 Toutefois, si vous convertissez une chaîne à **booléenne**, **unique**, ou **Double**, le type .NET Framework retourné n’est pas le même que le type retourné avec le **System.Convert** classe.  
  
## <a name="string-to-boolean"></a>String vers Boolean  
 Le tableau suivant indique le type généré pour la chaîne d’entrée donnée lors de la conversion d’une chaîne **booléenne** à l’aide de la **ToBoolean** (méthode).  
  
|Paramètre d'entrée de chaîne valide|Type de sortie .NET Framework|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 Examinons, par exemple, le code XML suivant :  
  
 **Entrée**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 Tous deux peuvent être reconnus par le code suivant, et **bvalue** est **System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>String vers Single  
 Le tableau suivant indique le type généré pour la chaîne d’entrée donnée lors de la conversion d’une chaîne à un **unique** à l’aide de la **ToSingle** (méthode).  
  
|Paramètre d'entrée de chaîne valide|Type de sortie .NET Framework|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>String vers Double  
 Le tableau suivant indique le type généré pour la chaîne d’entrée donnée lors de la conversion d’une chaîne à un **unique** à l’aide de la **ToDouble** (méthode).  
  
|Paramètre d'entrée de chaîne valide|Type de sortie .NET Framework|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 Le code suivant écrit `<Infinity>INF</Infinity>` :  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Conversion de Types de données XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [Conversion de Types .NET Framework en chaînes](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
