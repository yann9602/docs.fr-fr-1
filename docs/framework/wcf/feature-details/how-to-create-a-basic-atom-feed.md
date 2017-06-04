---
title: "Comment&#160;: cr&#233;er un flux Atom de base | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e0cacc1-9b11-4665-adb7-577a62626fd6
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Comment&#160;: cr&#233;er un flux Atom de base
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vous permet de créer un service qui expose un flux de syndication.Cette rubrique explique comment créer un service de syndication qui expose un flux de syndication Atom.  
  
### Pour créer un service de syndication de base  
  
1.  Définissez un contrat de service utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.Web.WebGetAttribute>.Chaque opération exposée comme un flux de syndication doit retourner un objet <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>.  
  
     [!code-csharp[htAtomBasic#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#0)]
     [!code-vb[htAtomBasic#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#0)]  
  
    > [!NOTE]
    >  Toutes les opérations du service qui appliquent <xref:System.ServiceModel.Web.WebGetAttribute> sont mappées aux demandes HTTP GET.Pour mapper votre opération à une méthode HTTP différente, utilisez <xref:System.ServiceModel.Web.WebInvokeAttribute> à la place.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Procédure : créer un service Web HTTP WCF de base](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md).  
  
2.  Implémentez le contrat de service.  
  
     [!code-csharp[htAtomBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#1)]
     [!code-vb[htAtomBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#1)]  
  
3.  Créez un objet <xref:System.ServiceModel.Syndication.SyndicationFeed> et ajoutez un auteur, une catégorie et une description.  
  
     [!code-csharp[htAtomBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#2)]
     [!code-vb[htAtomBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#2)]  
  
4.  Créez plusieurs objets <xref:System.ServiceModel.Syndication.SyndicationItem>.  
  
     [!code-csharp[htAtomBasic#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#3)]
     [!code-vb[htAtomBasic#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#3)]  
  
5.  Ajoutez les objets <xref:System.ServiceModel.Syndication.SyndicationItem> au flux.  
  
     [!code-csharp[htAtomBasic#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#4)]
     [!code-vb[htAtomBasic#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#4)]  
  
6.  Retournez le flux.  
  
     [!code-csharp[htAtomBasic#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#5)]
     [!code-vb[htAtomBasic#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#5)]  
  
### Pour héberger le service  
  
1.  Créez un objet <xref:System.ServiceModel.Web.WebServiceHost>.  
  
     [!code-csharp[htAtomBasic#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#6)]
     [!code-vb[htAtomBasic#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#6)]  
  
2.  Ouvrez l'hôte de service, chargez le flux à partir du service, affichez le flux et attendez que l'utilisateur appuie sur ENTRÉE.  
  
     [!code-csharp[htAtomBasic#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#8)]
     [!code-vb[htAtomBasic#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#8)]  
  
### Pour appeler GetBlog\(\) avec un HTTP GET  
  
1.  Ouvrez Internet Explorer, tapez l'URL suivante et appuyez sur ENTRÉE : http:\/\/localhost:8000\/BlogService\/GetBlog  
  
     L'URL contient l'adresse de base du service \(http:\/\/localhost:8000\/BlogService\), l'adresse relative du point de terminaison et l'opération de service à appeler.  
  
### Pour appeler GetBlog\(\) à partir d'un code  
  
1.  Créez un <xref:System.Xml.XmlReader> avec l'adresse de base et la méthode que vous appelez.  
  
     [!code-csharp[htAtomBasic#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#9)]
     [!code-vb[htAtomBasic#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#9)]  
  
2.  Appelez la méthode <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> statique, en passant dans le <xref:System.Xml.XmlReader> que vous venez de créer.  
  
     [!code-csharp[htAtomBasic#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#10)]
     [!code-vb[htAtomBasic#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#10)]  
  
     Cela appelle l'opération de service et remplit un nouvel objet <xref:System.ServiceModel.Syndication.SyndicationFeed> avec le module de formatage retourné à partir de l'opération de service.  
  
3.  Accédez à l'objet de flux.  
  
     [!code-csharp[htAtomBasic#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/snippets.cs#11)]
     [!code-vb[htAtomBasic#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/snippets.vb#11)]  
  
## Exemple  
 Les éléments suivants représentent l'intégralité du code pour cet exemple.  
  
 [!code-csharp[htAtomBasic#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatombasic/cs/program.cs#12)]
 [!code-vb[htAtomBasic#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatombasic/vb/program.vb#12)]  
  
## Compilation du code  
 Lors de la compilation du code précédent, référencez System.ServiceModel.dll et System.ServiceModel.Web.dll.  
  
## Voir aussi  
 <xref:System.ServiceModel.WebHttpBinding>   
 <xref:System.ServiceModel.Web.WebGetAttribute>