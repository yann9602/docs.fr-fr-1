---
title: "Proc&#233;dure&#160;: g&#233;n&#233;rer manuellement des classes de service de donn&#233;es client (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services de données WCF, bibliothèque cliente"
  - "Services de données WCF, configuration"
ms.assetid: b98cb1d6-956a-4e50-add6-67e4f2587346
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: g&#233;n&#233;rer manuellement des classes de service de donn&#233;es client (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] s'intègre à Visual Studio pour vous permettre de générer automatiquement des classes de service de données client lorsque vous utilisez la boîte de dialogue **Ajouter une référence de service** pour ajouter une référence à un service de données dans un projet Visual Studio.  Pour plus d'informations, consultez [Procédure : ajouter une référence de service de données](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  Vous pouvez également générer manuellement les mêmes classes de service de données client à l'aide de l'outil de génération du code, `DataSvcUtil.exe`. Cet outil, qui est inclus avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], génère des classes.NET Framework à partir de la définition d'un service de données.  Il peut également être utilisé pour générer des classes de service des données depuis le fichier de modèle conceptuel \(.csdl\) et depuis le fichier .edmx qui représente un modèle Entity Framework dans un projet Visual Studio.  
  
 L'exemple dans cette rubrique crée des classes de service de données client basées sur l'exemple de service de données Northwind.  Ce service est créé lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  Certains exemples dans cette rubrique requièrent le fichier modèle conceptuel pour le modèle Northwind.  Pour plus d'informations, consultez [Procédure : utiliser EdmGen.exe pour générer les fichiers de modèle et de mappage \(Entity Framework\)](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  Certains exemples dans cette rubrique requièrent le fichier .edmx pour le modèle Northwind.  Pour plus d'informations, consultez [.edmx File Overview](http://msdn.microsoft.com/fr-fr/f4c8e7ce-1db6-417e-9759-15f8b55155d4).  
  
### Pour générer des classes C\# qui prennent en charge la liaison de données  
  
-   À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:CSharp /out:Northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .  
  
### Pour générer des classes Visual Basic qui prennent en charge la liaison de données  
  
-   À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /dataservicecollection /version:2.0 /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .  
  
### Pour générer des classes C\# basées sur l'URI de service  
  
-   À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\DataSvcUtil.exe" /language:CSharp /out:northwind.cs /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .  
  
### Pour générer des classes Visual Basic basées sur l'URI de service  
  
-   À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /out:Northwind.vb /uri:http://localhost:12345/Northwind.svc  
    ```  
  
    > [!NOTE]
    >  Vous devez remplacer la valeur fournie au paramètre `/uri:` par l'URI de l'instance de votre exemple de service de données Northwind .  
  
### Pour générer des classes C\# basées sur le fichier de modèle conceptuel \(CSDL\)  
  
-   À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.csdl /out:Northwind.cs  
    ```  
  
### Pour générer des classes Visual Basic basées sur le fichier de modèle conceptuel \(CSDL\)  
  
-   À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.csdl /out:Northwind.vb  
    ```  
  
### Pour générer des classes C\# basées sur le fichier .edmx  
  
-   À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:CSharp /in:Northwind.edmx /out:c:\northwind.cs   
    ```  
  
### Pour générer des classes Visual Basic basées sur le fichier .edmx  
  
-   À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v3.5\datasvcutil.exe" /language:VB /in:Northwind.edmx /out:c:\northwind.vb   
    ```  
  
## Voir aussi  
 [Génération de la bibliothèque cliente du service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)   
 [Procédure : ajouter une référence de service de données](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)   
 [Utilitaire client WCF Data Services \(DataSvcUtil.exe\)](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)