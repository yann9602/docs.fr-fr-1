---
title: "JSON Serialization | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# JSON Serialization
Cet exemple montre comment utiliser le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pour sérialiser et désérialiser des données au format JSON \(JavaScript Objet Notation\).Ce moteur de sérialisation convertit des données JSON en instances de types [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] et à nouveau en données JSON.<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> prend en charge les mêmes types que <xref:System.Runtime.Serialization.DataContractSerializer>.Le format de données JSON est particulièrement utile lors de l'écriture d'applications Web de style JavaScript et XML \(AJAX\) asynchrones.La prise en charge d'AJAX dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est optimisée pour permettre son utilisation avec ASP.NET AJAX via le contrôle ScriptManager.Pour obtenir des exemples d'utilisation de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] avec AJAX ASP.NET, consultez les [AJAX Samples](http://msdn.microsoft.com/fr-fr/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
 L'exemple utilise un contrat de données `Person` pour illustrer la sérialisation et la désérialisation.  
  
```  
[DataContract]  
    class Person  
    {  
        [DataMember]  
        internal string name;  
  
        [DataMember]  
        internal int age;  
    }  
  
```  
  
 Pour sérialiser une instance du type `Person` en JSON, créez d'abord le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> et utilisez la méthode `WriteObject` pour écrire des données JSON dans un flux.  
  
```  
Person p = new Person();  
//Set up Person object...  
MemoryStream stream1 = new MemoryStream();  
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
ser.WriteObject(stream1, p);  
  
```  
  
 Le flux de mémoire contient des données JSON valides.  
  
```  
{“age”:42,”name”:”John”}  
  
```  
  
 L'exemple illustre la désérialisation de données JSON dans un objet.Ensuite, vous rembobinez le flux et appelez `ReadObject`.  
  
```  
Person p2 = (Person)ser.ReadObject(stream1);  
```  
  
 L'examen de l'objet `p2` révèle que les données JSON ont été correctement désérialisées.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Générez la solution JsonSerialization.sln telle que décrite dans la section [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Exécutez l'application console qui en résulte.  
  
## Voir aussi