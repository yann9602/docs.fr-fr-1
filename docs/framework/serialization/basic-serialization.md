---
title: "S&#233;rialisation de base | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sérialisation binaire, sérialisation de base"
  - "sérialisation, sérialisation de base"
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# S&#233;rialisation de base
La façon la plus simple de rendre une classe sérialisable est de la marquer avec l'attribut [Serializable](frlrfSystemSerializableAttributeClassTopic) comme suit.  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
 L'exemple de code suivant illustre la manière dont une instance de cette classe peut être sérialisée dans un fichier.  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
 Cet exemple utilise un formateur binaire pour effectuer la sérialisation.Il vous suffit de créer une instance du flux de données et du formateur que vous envisagez d'utiliser puis d'appeler la méthode **Serialize** sur le formateur.Le flux de données et l'objet à sérialiser sont fournis comme paramètres de cet appel.Bien que cela n'apparaisse pas explicitement dans cet exemple, toutes les variables membres d'une classe seront sérialisées, même celles marquées comme privées.Dans ce cadre, la sérialisation binaire diffère de la [classe XMLSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) qui sérialise uniquement des champs publics.Pour plus d'informations sur l'exclusion de variables membres de la sérialisation binaire, consultez [Sérialisation sélective](../../../docs/framework/serialization/selective-serialization.md).  
  
 La restauration de l'objet à son état précédent est très facile.En premier lieu, créez un flux de données servant à la lecture et un [formateur](frlrfSystemRuntimeSerializationFormatterClassTopic) puis demandez à ce dernier de désérialiser l'objet.L'exemple de code suivant illustre cette procédure.  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
 Le [BinaryFormatter](frlrfSystemRuntimeSerializationFormattersBinaryBinaryFormatterClassTopic) utilisé ci\-dessus est très efficace et génère un flux d'octets compact.Ce formateur permet aussi bien de sérialiser que de désérialiser des objets, ce qui en fait l'outil idéal pour sérialiser des objets qui seront désérialisés sur le .NET Framework.Il est important de noter que les constructeurs ne sont pas appelés lorsqu'un objet est désérialisé.Pour des raisons de performances, la désérialisation repose sur cette contrainte.Toutefois, cela enfreint les termes de certains contrats habituels que l'exécution passe avec le writer d'objets et les développeurs doivent s'assurer qu'ils comprennent les ramifications lorsqu'ils marquent un objet comme sérialisable.  
  
 Si la portabilité est une spécification, utilisez plutôt le [SoapFormatter](frlrfSystemRuntimeSerializationFormattersSoapSoapFormatterClassTopic).Remplacez simplement le **BinaryFormatter** dans le code ci\-dessus par **SoapFormatter,** et appelez **Serialize** et **Deserialize** comme précédemment.Ce formateur génère le résultat suivant pour l'exemple utilisé ci\-dessus.  
  
```  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:SOAP- ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP- ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle=  
  "http://schemas.microsoft.com/soap/encoding/clr/1.0"  
  "http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
 Il est important de noter que l'attribut **Serializable** ne peut pas être hérité.Si vous dérivez une nouvelle classe à partir de `MyObject`, elle doit également être marquée avec l'attribut. Sinon, elle ne peut pas être sérialisée.Par exemple, lorsque vous tentez de sérialiser une instance de la classe ci\-dessous, vous obtenez un [SerializationException](frlrfSystemRuntimeSerializationSerializationExceptionClassTopic) informant que le type `MyStuff` n'est pas marqué comme sérialisable.  
  
```csharp  
public class MyStuff : MyObject   
{  
  public int n3;  
}  
```  
  
 L'utilisation de l'attribut **Serializable** est pratique, mais comporte des limites comme illustré précédemment.Reportez\-vous aux [Indications concernant la sérialisation](../../../docs/framework/serialization/serialization-guidelines.md) pour savoir à quel moment il convient de marquer une classe en vue de la sérialisation. La sérialisation ne peut pas être ajoutée à une classe une fois que cette dernière a été compilée.  
  
## Voir aussi  
 [Sérialisation binaire](../../../docs/framework/serialization/binary-serialization.md)   
 [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58)   
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)