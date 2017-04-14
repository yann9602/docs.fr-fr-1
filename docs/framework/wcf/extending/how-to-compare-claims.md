---
title: "Comment&#160;: comparer des revendications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "revendications (WCF)"
  - "revendications (WCF), comparer"
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Comment&#160;: comparer des revendications
L'infrastructure de modèle d'identité dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est utilisée pour effectuer les contrôles d'autorisation.L'une des tâches fréquentes de cette infrastructure de contrôle consiste notamment à comparer les revendications émises dans le cadre des autorisations à celles requises pour l'exécution des requêtes d'action ou des requêtes d'accès aux ressources.Cette rubrique contient des instructions qui permettent de comparer des revendications, notamment les types de revendication intégrés et personnalisés.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'infrastructure de modèle d'identité, consultez [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
 Comparer des revendications signifie comparer leurs trois composantes, à savoir leur type, leurs droits et leurs ressources avec les composantes d'autres revendications, et ce afin de savoir si elles sont égales.Lisez l'exemple suivant.  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 Ces deux revendications partagent le même type de revendication <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, les mêmes droits <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> et une même ressource pour la chaîne "someone".Leurs trois composantes étant égales, ces deux revendications sont elles\-mêmes égales.  
  
 Les types de revendication intégrés sont comparés à l'aide de la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A>.Un code de comparaison spécifique à la revendication est utilisé lorsque nécessaire.Prenons, par exemple, les deux revendications suivantes qui utilisent un nom d'utilisateur principal \(UPN, User Principal Name\) :  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 Le code de comparaison de la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A> retourne la valeur `true` car il suppose que `example\someone` permet d'identifier le même utilisateur de domaine que « xyz@exemple.fr ».  
  
 Les types de revendication personnalisés peuvent également être comparés à l'aide de la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A>.Toutefois, si le type retourné par la propriété <xref:System.IdentityModel.Claims.Claim.Resource%2A> de la revendication est un type autre que primitif, la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A> retournera uniquement la valeur `true` si les valeurs retournées par les propriétés `Resource` sont égales selon la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A>.Dans les cas où ce processus ne convient pas, le type personnalisé retourné par la propriété `Resource` doit remplacer les méthodes <xref:System.IdentityModel.Claims.Claim.Equals%2A> et <xref:System.Object.GetHashCode%2A> afin de permettre tous traitements personnalisés requis.  
  
### Comparaison des revendications intégrées  
  
1.  Soit deux instances de la classe <xref:System.IdentityModel.Claims.Claim>, utilisez la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A> pour les comparer, tel qu'illustré dans le code suivant.  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### Comparaison de revendications personnalisées dont les types de ressources sont primitifs  
  
1.  Pour les revendications personnalisées dont les types de ressources sont primitifs, la comparaison peut s'effectuer de la même manière que dans le cadre de comparaisons intégrées, tel qu'illustré dans le code suivant.  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  Pour les revendications personnalisées dont les types de ressources sont basés sur une structure ou une classe, le type de ressource doit être substitué à la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A>.  
  
3.  Vérifiez tout d'abord si le paramètre `obj` a la valeur `null`. Si tel est le cas, retournez la valeur `false`.  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  Appelez ensuite la méthode <xref:System.Object.ReferenceEquals%2A> et passez `this` et `obj` en tant que paramètres.Si la méthode appelée retourne la valeur `true`, retournez alors la valeur `true`.  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  Essayez ensuite d'affecter `obj` à une variable locale du type de classe.En cas d'échec, la référence est `null`.Dans ce cas, retournez la valeur `false`.  
  
6.  Effectuez la comparaison personnalisée nécessaire pour comparer de manière adéquate la revendication en cours à la revendication spécifiée.  
  
## Exemple  
 L'exemple suivant illustre le cas d'une comparaison où le type de ressource des revendications personnalisées comparées n'est pas primitif.  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## Voir aussi  
 [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)   
 [Comment : créer une revendication personnalisée](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)