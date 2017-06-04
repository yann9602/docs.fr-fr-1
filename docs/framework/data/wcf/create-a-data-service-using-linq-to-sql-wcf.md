---
title: "Proc&#233;dure&#160;: cr&#233;er un service de donn&#233;es &#224; l&#39;aide d&#39;une source de donn&#233;es LINQ to SQL (WCF Data Services) | Microsoft Docs"
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
  - "Services de données WCF, LINQ to SQL"
  - "Services de données WCF, fournisseurs"
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: cr&#233;er un service de donn&#233;es &#224; l&#39;aide d&#39;une source de donn&#233;es LINQ to SQL (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] expose les données d'entité comme un service de données.  Le fournisseur de réflexion vous permet de définir un modèle de données basé sur toute classe exposant des membres qui retournent une implémentation <xref:System.Linq.IQueryable%601>.  Pour pouvoir effectuer des mises à jour des données dans la source de données, ces classes doivent également implémenter l'interface <xref:System.Data.Services.IUpdatable>.  Pour plus d'informations, consultez [fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  Cette rubrique vous montre comment créer des classes LINQ to SQL qui accèdent à l'exemple de base de données Northwind à l'aide du fournisseur de réflexion, et comment créer le service de données basé sur ces classes de données.  
  
### Pour ajouter des classes LINQ to SQL à un projet.  
  
1.  À partir d'une application Visual Basic ou C\#, dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Cliquez sur le modèle **Classes LINQ to SQL**.  
  
3.  Modifiez le nom en Northwind.dbml.  
  
4.  Cliquez sur **Ajouter**.  
  
     Le fichier Northwind.dbml est ajouté au projet et le Concepteur Objet\/Relationnel \(Concepteur O\/R\) s'ouvre.  
  
5.  Dans **Serveur**\/**Explorateur de bases de données**, sous Northwind, développez **Tables** et faites glisser la table `Customers` vers le Concepteur Objet\/Relationnel \(Concepteur O\/R\).  
  
     Une classe d'entité `Customer` est créée et apparaît dans l'aire de conception.  
  
6.  Répétez l'étape 6 pour les tables `Orders`, `Order_Details` et `Products`.  
  
7.  Cliquez avec le bouton droit sur le nouveau fichier .dbml qui représente les classes LINQ to SQL et cliquez sur **Afficher le code**.  
  
     Cela crée une nouvelle page code\-behind nommée Northwind.cs qui contient une définition de classe partielle pour la classe qui hérite de la classe <xref:System.Data.Linq.DataContext>, dans ce cas `NorthwindDataContext`.  
  
8.  Remplacez le contenu du fichier de code Northwind.cs par le code suivant.  Ce code implémente le fournisseur de réflexion en étendant les classes de données et <xref:System.Data.Linq.DataContext> générés par LINQ to SQL :  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### Pour créer un service de données en utilisant un modèle de données LINQ to SQL  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom de votre projet ASP.NET, puis cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Service de données WCF**.  
  
3.  Fournissez un nom pour le service, puis cliquez sur **OK**.  
  
     Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service.  La fenêtre de l'éditeur de code s'ouvre par défaut.  
  
4.  Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindDataContext`.  
  
5.  Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     Cela permet aux clients autorisés d'accéder aux ressources pour les trois jeux d'entités spécifiés.  
  
6.  Pour tester le service de données Northwind.svc à l'aide d'un navigateur Web, suivez les instructions dans la rubrique [Accès au service à partir d'un navigateur Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## Voir aussi  
 [Procédure : créer un service de données à l'aide d'une source de données ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)   
 [Procédure : créer un service de données à l'aide du fournisseur de réflexion](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)   
 [fournisseurs de services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)