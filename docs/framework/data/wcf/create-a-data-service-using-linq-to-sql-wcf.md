---
title: "Comment : créer un service de données à l'aide d'un LINQ vers la source de données SQL (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52529689242342afa8920a7b01b532a24337f562
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>Comment : créer un service de données à l'aide d'un LINQ vers la source de données SQL (services de données WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] expose les données d'entité comme un service de données. Le fournisseur de réflexion vous permet de définir un modèle de données qui est basé sur toute classe qui expose des membres qui retournent un <xref:System.Linq.IQueryable%601> mise en œuvre. Pour pouvoir effectuer des mises à jour des données dans la source de données, ces classes doivent également implémenter l'interface <xref:System.Data.Services.IUpdatable>. Pour plus d’informations, consultez [des fournisseurs de Services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md). Cette rubrique vous montre comment créer des classes LINQ to SQL qui accèdent à l'exemple de base de données Northwind à l'aide du fournisseur de réflexion, et comment créer le service de données basé sur ces classes de données.  
  
### <a name="to-add-linq-to-sql-classes-to-a-project"></a>Pour ajouter des classes LINQ to SQL à un projet.  
  
1.  À partir d’une application Visual Basic ou c#, sur le **projet** menu, cliquez sur **ajouter un nouvel élément**.  
  
2.  Cliquez sur le **Classes LINQ to SQL** modèle.  
  
3.  Remplacez le nom par **Northwind.dbml**.  
  
4.  Cliquez sur **Ajouter**.  
  
     Le fichier Northwind.dbml est ajouté au projet et le Concepteur Objet/Relationnel (Concepteur O/R) s'ouvre.  
  
5.  Dans **Server**/**l’Explorateur de base de données**, sous Northwind, développez **Tables** et faites glisser le `Customers` table sur le Concepteur Objet/Relationnel (O/R Concepteur).  
  
     Une classe d'entité `Customer` est créée et apparaît dans l'aire de conception.  
  
6.  Répétez l'étape 6 pour les tables `Orders`, `Order_Details` et `Products`.  
  
7.  Cliquez sur le nouveau fichier .dbml qui représente le LINQ de classes SQL et cliquez sur **afficher le Code**.  
  
     Cela crée une nouvelle page code-behind nommée Northwind.cs qui contient une définition de classe partielle pour la classe qui hérite de la classe <xref:System.Data.Linq.DataContext>, dans ce cas `NorthwindDataContext`.  
  
8.  Remplacez le contenu du fichier de code Northwind.cs par le code suivant. Ce code implémente le fournisseur de réflexion en étendant les classes de données et <xref:System.Data.Linq.DataContext> générés par LINQ to SQL :  
  
     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.vb#linq2sqlprovider)]  
  
### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>Pour créer un service de données en utilisant un modèle de données LINQ to SQL  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le nom de votre projet ASP.NET, puis cliquez sur **ajouter un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Service de données WCF**.  
  
3.  Fournissez un nom pour le service, puis cliquez sur **OK**.  
  
     Visual Studio crée le balisage XML et des fichiers de code pour le nouveau service. La fenêtre de l'éditeur de code s'ouvre par défaut.  
  
4.  Dans le code du service de données, remplacez le commentaire `/* TODO: put your data source class name here */` dans la définition de la classe qui définit le service de données par le type qui est le conteneur d'entités du modèle de données, dans ce cas `NorthwindDataContext`.  
  
5.  Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :  
  
     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria linq provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria linq provider/vb/northwind.svc.vb#enableaccess)]  
  
     Cela permet aux clients autorisés d'accéder aux ressources pour les trois jeux d'entités spécifiés.  
  
6.  Pour tester le service de données Northwind.svc à l’aide d’un navigateur Web, suivez les instructions de la rubrique [l’accès au Service à partir d’un navigateur Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un Service de données à l’aide d’une Source de données ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)  
 [Comment : créer un Service de données à l’aide du fournisseur de réflexion](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
 [Fournisseurs de Services de données](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
