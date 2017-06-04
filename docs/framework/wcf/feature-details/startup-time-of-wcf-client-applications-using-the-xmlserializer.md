---
title: "Comment&#160;: am&#233;liorer le temps de d&#233;marrage des applications clientes WCF &#224; l&#39;aide de XmlSerializer | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Comment&#160;: am&#233;liorer le temps de d&#233;marrage des applications clientes WCF &#224; l&#39;aide de XmlSerializer
Les applications clientes et de services qui utilisent des types de données sérialisables à l'aide de <xref:System.Xml.Serialization.XmlSerializer> génèrent et compilent le code de sérialisation de ces types de données lors de l'exécution, ce qui peut provoquer des performances de démarrage lentes.  
  
> [!NOTE]
>  Le code de sérialisation prégénéré est réservé aux applications clientes, pas aux services.  
  
 [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) peut améliorer les performances de démarrage de ces applications en générant le code de sérialisation nécessaire à partir des assemblys compilés pour l'application.Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.Les contrats de service et d'opération qui utilisent <xref:System.Xml.Serialization.XmlSerializer> sont marqués avec <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### Pour générer du code de sérialisation XmlSerializer.  
  
1.  Compilez votre code de service ou client dans un ou plusieurs assemblys.  
  
2.  Ouvrez une invite de commandes du Kit de développement SDK.  
  
3.  À l'invite de commandes, lancez l'outil Svcutil.exe à l'aide du format suivant.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     L'argument `assemblyPath` spécifie le chemin d'accès à un assembly contenant des types de contrat de service.Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe peut uniquement générer du code de sérialisation C\#.Un fichier de code source est généré pour chaque assembly d'entrée.Vous ne pouvez pas utiliser le commutateur **\/language** pour modifier le langage du code généré.  
  
     Pour spécifier le chemin d'accès aux assemblys dépendants, utilisez l'option **\/reference**.  
  
4.  Rendez le code de sérialisation généré disponible pour votre application en utilisant l'une des options suivantes :  
  
    1.  Compilez le code de sérialisation généré dans un assembly séparé portant le nom \[*original assembly*\].XmlSerializers.dll \(par exemple, MyApp.XmlSerializers.dll\).Votre application doit être en mesure de charger l'assembly, qui doit être signé avec la même clé que l'assembly d'origine.Si vous recompilez l'assembly d'origine, vous devez régénérer l'assembly de sérialisation.  
  
    2.  Compilez le code de sérialisation généré dans un assembly distinct et utilisez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> sur le contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>.Définissez les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> pour pointer vers l'assembly de sérialisation compilé.  
  
    3.  Compilez le code de sérialisation généré dans votre assembly d'application et ajoutez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> au contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>.Ne définissez pas les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>.L'assembly de sérialisation par défaut est supposé être l'assembly actuel.  
  
## Exemple  
 La commande suivante génère des types de sérialisation pour les types `XmlSerializer` que les contrats de service de l'assembly utilisent.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## Voir aussi  
 [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)