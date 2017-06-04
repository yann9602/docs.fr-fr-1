---
title: "Applications clientes s&#233;curis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Applications clientes s&#233;curis&#233;es
Les applications se composent généralement de nombreuses parties qui doivent toutes être protégées face aux vulnérabilités susceptibles d'entraîner une perte de données ou compromettre d'une autre manière le système.  La création d'interfaces utilisateur sécurisées peut empêcher de nombreux problèmes en bloquant les attaquants avant qu'ils puissent accéder aux données ou aux ressources système.  
  
## Valider les entrées d'utilisateur  
 Lors de la construction d'une application qui accède à des données, vous devez vous baser sur l'hypothèse que toute entrée d'utilisateur est malveillante jusqu'à preuve du contraire.  Si vous ne le faites pas, votre application sera vulnérable aux attaques.  Le .NET Framework contient des classes pour vous aider à appliquer un domaine de valeurs pour les contrôles d'entrées, comme la limitation du nombre de caractères qui peuvent être entrés.  Les connexions d'événement vous permettent d'écrire des procédures pour contrôler la validité des valeurs.  Les données d'entrée d'utilisateur peuvent être validées et fortement typées, ce qui limite l'exposition d'une application aux attaques de script et par injection de code SQL.  
  
> [!IMPORTANT]
>  Vous devez également valider l'entrée d'utilisateur au niveau de la source de données, ainsi que dans l'application cliente.  Un attaquant peut choisir de contourner votre application et d'attaquer la source de données directement.  
  
 [Sécurité et entrées d'utilisateur](../../../../docs/standard/security/security-and-user-input.md)  
 Explique comment gérer des bogues subtils et potentiellement dangereux qui impliquent une entrée d'utilisateur.  
  
 [Validating User Input in ASP.NET Web Pages](../Topic/Validating%20User%20Input%20in%20ASP.NET%20Web%20Pages.md)  
 Vue d'ensemble de la validation d'une entrée d'utilisateur à l'aide des contrôles de validation ASP.NET.  
  
 [Entrées d'utilisateur dans les Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)  
 Fournit des liens et des informations relatifs à la validation des entrées de la souris et au clavier dans une application Windows Forms.  
  
 [Expressions régulières du .NET Framework](../../../../docs/standard/base-types/regular-expressions.md)  
 Explique comment utiliser la classe <xref:System.Text.RegularExpressions.Regex> pour vérifier la validité des entrées d'utilisateur.  
  
## Applications Windows  
 Auparavant, les applications Windows s'exécutaient généralement avec toutes les autorisations.  Le .NET Framework fournit l'infrastructure permettant de restreindre l'exécution du code dans une application Windows en utilisant la sécurité d'accès du code.  Toutefois, la sécurité d'accès du code seule n'est pas suffisante pour protéger votre application.  
  
 [Sécurité des Windows Forms](../../../../docs/framework/winforms/windows-forms-security.md)  
 Explique comment sécuriser des applications Windows Forms et fournit des liens vers des rubriques connexes.  
  
 [Applications Windows Forms et non managées](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Explique comment interagir avec des applications non managées dans une application Windows Forms.  
  
 [ClickOnce Deployment for Windows Forms Applications](http://msdn.microsoft.com/fr-fr/34d8c770-48f2-460c-8d67-4ea5684511df)  
 Explique comment utiliser un déploiement `ClickOnce` dans une application Windows Forms et traite des implications en matière de sécurité.  
  
## ASP.NET et services Web XML  
 Les applications ASP.NET doivent généralement restreindre l'accès à certaines portions du site Web et fournissent d'autres mécanismes de protection des données et de sécurité du site.  Ces liens fournissent des informations utiles pour sécuriser votre application ASP.NET.  
  
 Un service Web XML fournit des données qui peuvent être consommées par une application ASP.NET, une application Windows Forms ou un autre service Web.  Vous devez gérer la sécurité pour le service Web lui\-même, ainsi que la sécurité pour l'application cliente.  
  
 Pour plus d'informations, voir les ressources ci\-dessous.  
  
|Ressource|Description|  
|---------------|-----------------|  
|[NIB: ASP.NET Security](http://msdn.microsoft.com/fr-fr/04b37532-18d9-40b4-8e5f-ee09a70b311d)|Explique comment sécuriser des applications ASP.NET.|  
|[Securing XML Web Services Created Using ASP.NET](http://msdn.microsoft.com/fr-fr/354b2ab1-2782-4542-b32a-dc560178b90c)|Explique comment implémenter la sécurité pour un service Web ASP.NET.|  
|[Script Exploits Overview](../Topic/Script%20Exploits%20Overview.md)|Explique comment se protéger d'une attaque de script, qui tente d'insérer des caractères nuisibles dans une page Web.|  
|[NIB:Basic Security Practices for ASP.NET Web Applications](http://msdn.microsoft.com/fr-fr/94a52ab8-731d-417e-b997-721baf43df38)|Informations générales sur la sécurité et liens vers une présentation additionnelle.|  
  
## Communication à distance  
 .NET Remoting vous permet de créer aisément des applications largement distribuées, que les composants d'application se trouvent tous sur un même ordinateur ou soient dispersés dans le monde entier.  Vous pouvez générer des applications clientes qui utilisent des objets dans d'autres processus sur le même ordinateur ou sur tout autre ordinateur qui est accessible sur son réseau.  Vous pouvez également utiliser .NET Remoting pour communiquer avec d'autres domaines d'application dans le même processus.  
  
|Ressource|Description|  
|---------------|-----------------|  
|[Configuration of Remote Applications](http://msdn.microsoft.com/fr-fr/92c0c097-d984-4315-835b-7490ecdf1097)|Explique comment configurer les applications de communication à distance pour éviter les problèmes courants.|  
|[Security in Remoting](http://msdn.microsoft.com/fr-fr/9574262c-d4b1-41c5-8600-24ff147c0add)|Décrit l'authentification et le chiffrement, ainsi que des rubriques de sécurité supplémentaires relatives à la communication à distance.|  
|[Considérations sur la sécurité et la communication à distance](../../../../docs/framework/misc/security-and-remoting-considerations.md)|Décrit les problèmes de sécurité liés aux objets protégés et au franchissement de domaine d'application.|  
  
## Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [Recommendations for Data Access Strategies](http://msdn.microsoft.com/fr-fr/72411f32-d12a-4de8-b961-e54fca7faaf5)   
 [Sécurisation des applications](../Topic/Securing%20Applications.md)   
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)