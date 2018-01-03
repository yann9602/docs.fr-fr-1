---
title: "Applications clientes sécurisées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1218cda46a6a901c3dbf9fb11333b04d0133df42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="secure-client-applications"></a>Applications clientes sécurisées
Les applications se composent généralement de nombreuses parties qui doivent toutes être protégées face aux vulnérabilités susceptibles d'entraîner une perte de données ou compromettre d'une autre manière le système. La création d'interfaces utilisateur sécurisées peut empêcher de nombreux problèmes en bloquant les attaquants avant qu'ils puissent accéder aux données ou aux ressources système.  
  
## <a name="validate-user-input"></a>Valider les entrées d'utilisateur  
 Lors de la construction d'une application qui accède à des données, vous devez vous baser sur l'hypothèse que toute entrée d'utilisateur est malveillante jusqu'à preuve du contraire. Si vous ne le faites pas, votre application sera vulnérable aux attaques. Le .NET Framework contient des classes pour vous aider à appliquer un domaine de valeurs pour les contrôles d'entrées, comme la limitation du nombre de caractères qui peuvent être entrés. Les connexions d'événement vous permettent d'écrire des procédures pour contrôler la validité des valeurs. Les données d'entrée d'utilisateur peuvent être validées et fortement typées, ce qui limite l'exposition d'une application aux attaques de script et par injection de code SQL.  
  
> [!IMPORTANT]
>  Vous devez également valider l'entrée d'utilisateur au niveau de la source de données, ainsi que dans l'application cliente. Un attaquant peut choisir de contourner votre application et d'attaquer la source de données directement.  
  
 [Sécurité et entrées d’utilisateur](../../../../docs/standard/security/security-and-user-input.md)  
 Explique comment gérer des bogues subtils et potentiellement dangereux qui impliquent une entrée d'utilisateur.  
  
 [Validation des entrées d’utilisateur dans les Pages Web ASP.NET](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461)  
 Vue d’ensemble de la validation d’une entrée d’utilisateur à l’aide des contrôles de validation ASP.NET.  
  
 [Entrées d’utilisateur dans les Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Fournit des liens et des informations relatifs à la validation des entrées de la souris et au clavier dans une application Windows Forms.  
  
 [.NET Framework (expressions régulières)](../../../../docs/standard/base-types/regular-expressions.md)  
 Explique comment utiliser la classe <xref:System.Text.RegularExpressions.Regex> pour vérifier la validité des entrées d'utilisateur.  
  
## <a name="windows-applications"></a>Applications Windows  
 Auparavant, les applications Windows s'exécutaient généralement avec toutes les autorisations. Le .NET Framework fournit l'infrastructure permettant de restreindre l'exécution du code dans une application Windows en utilisant la sécurité d'accès du code. Toutefois, la sécurité d'accès du code seule n'est pas suffisante pour protéger votre application.  
  
 [Sécurité de Windows Forms](../../../../docs/framework/winforms/windows-forms-security.md)  
 Explique comment sécuriser des applications Windows Forms et fournit des liens vers des rubriques connexes.  
  
 [Applications Windows Forms et non managées](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Explique comment interagir avec des applications non managées dans une application Windows Forms.  
  
 [Applications de déploiement de ClickOnce pour les Windows Forms](http://msdn.microsoft.com/en-us/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Explique comment utiliser un déploiement `ClickOnce` dans une application Windows Forms et traite des implications en matière de sécurité.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET et services Web XML  
 Les applications ASP.NET doivent généralement restreindre l'accès à certaines portions du site Web et fournissent d'autres mécanismes de protection des données et de sécurité du site. Ces liens fournissent des informations utiles pour sécuriser votre application ASP.NET.  
  
 Un service Web XML fournit des données qui peuvent être consommées par une application ASP.NET, une application Windows Forms ou un autre service Web. Vous devez gérer la sécurité pour le service Web lui-même, ainsi que la sécurité pour l'application cliente.  
  
 Pour plus d'informations, voir les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[NIB : ASP.NET sécurité](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d)|Explique comment sécuriser des applications ASP.NET.|  
|[Sécurisation des Services Web XML créés à l’aide d’ASP.NET](http://msdn.microsoft.com/en-us/354b2ab1-2782-4542-b32a-dc560178b90c)|Explique comment implémenter la sécurité pour un service Web ASP.NET.|  
|[Vue d’ensemble des attaques de script](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Explique comment se protéger d’une attaque de script, qui tente d’insérer des caractères nuisibles dans une page web.|  
|[NIB : Basic les pratiques de sécurité pour les Applications Web ASP.NET](http://msdn.microsoft.com/en-us/94a52ab8-731d-417e-b997-721baf43df38)|Informations générales sur la sécurité et liens vers une présentation additionnelle.|  
  
## <a name="remoting"></a>Communication à distance  
 .NET Remoting vous permet de créer aisément des applications largement distribuées, que les composants d'application se trouvent tous sur un même ordinateur ou soient dispersés dans le monde entier. Vous pouvez générer des applications clientes qui utilisent des objets dans d'autres processus sur le même ordinateur ou sur tout autre ordinateur qui est accessible sur son réseau. Vous pouvez également utiliser .NET Remoting pour communiquer avec d'autres domaines d'application dans le même processus.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Configuration des Applications à distance](http://msdn.microsoft.com/en-us/92c0c097-d984-4315-835b-7490ecdf1097)|Explique comment configurer les applications de communication à distance pour éviter les problèmes courants.|  
|[Sécurité de la communication à distance](http://msdn.microsoft.com/en-us/9574262c-d4b1-41c5-8600-24ff147c0add)|Décrit l'authentification et le chiffrement, ainsi que des rubriques de sécurité supplémentaires relatives à la communication à distance.|  
|[Sécurité et des considérations relatives à la communication à distance](../../../../docs/framework/misc/security-and-remoting-considerations.md)|Décrit les problèmes de sécurité liés aux objets protégés et au franchissement de domaine d'application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Recommandations pour les stratégies d’accès aux données](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Sécurisation des applications](/visualstudio/ide/securing-applications)  
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
