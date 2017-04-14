---
title: "Utilisation de biblioth&#232;ques &#224; partir de code d&#39;un niveau de confiance partiel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AllowPartiallyTrustedCallersAttribute (attribut)"
  - "APTCA"
  - "sécurité d'accès du code, code d'un niveau de confiance partiel"
  - "confiance partielle"
  - "code d'un niveau de confiance partiel"
  - "sécurité (.NET Framework), code d'un niveau de confiance partiel"
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: 25
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 23
---
# Utilisation de biblioth&#232;ques &#224; partir de code d&#39;un niveau de confiance partiel
> [!NOTE]
>  Cette rubrique aborde le comportement des assemblys avec nom fort et s'applique uniquement aux assemblys de [niveau 1](../../../docs/framework/misc/security-transparent-code-level-1.md). Les assemblys de [Code transparent de sécurité, niveau 2](../../../docs/framework/misc/security-transparent-code-level-2.md) de [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ou versions ultérieures ne sont pas affectés par les noms forts. Pour plus d’informations sur les modifications apportées au système de sécurité, consultez [Modifications de sécurité](../../../docs/framework/security/security-changes.md).  
  
> [!CAUTION]
>  Sécurité d'accès du code et code d'un niveau de confiance partiel  
>   
>  Le .NET Framework fournit un mécanisme, appelé « sécurité d'accès du code \(CAS\) », qui permet de mettre en œuvre différents niveaux de confiance sur différents codes exécutés dans la même application.  La sécurité d'accès du code dans .NET Framework ne doit pas être utilisée comme limite de sécurité avec du code d'un niveau de confiance partiel, notamment du code d'origine inconnue. Nous vous déconseillons de charger et d'exécuter du code d'origine inconnue sans mettre en place d'autres mesures de sécurité.  
>   
>  Cette stratégie s'applique à toutes les versions du .NET Framework, mais ne concerne pas le .NET Framework inclus dans Silverlight.  
  
 Les applications qui n’ont pas reçu un niveau de confiance totale de la part de leur hôte ou bac à sable \(sandbox\) ne sont pas autorisées à appeler les bibliothèques managées partagées, sauf si le créateur de la bibliothèque les autorise explicitement à passer outre l’utilisation de l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute>. Par conséquent, les auteurs d'applications doivent être conscients que certaines bibliothèques pas seront disponibles dans un contexte de confiance partielle. Par défaut, tout le code qui s'exécute dans un [bac à sable \(sandbox\)](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) de confiance partiel et qui n'est pas dans la liste des assemblys de confiance totale dispose d'un niveau de confiance partielle. S'il n'est pas prévu que votre code soit exécuté dans un contexte de confiance partielle ou qu'il soit appelé par du code partiellement fiable, les informations de cette section ne vous concernent pas. Toutefois, si vous écrivez du code qui doit interagir avec du code partiellement fiable ou fonctionner dans un contexte de confiance partiel, vous devez prendre en compte les éléments suivants :  
  
-   Les bibliothèques doivent être signées avec un nom fort pour pouvoir être partagées par plusieurs applications. Les noms forts permettent à votre code d'être placé dans un Global Assembly Cache ou d'être ajouté à la liste de confiance totale d'un bac à sable <xref:System.AppDomain>. De plus, ils permettent aux utilisateurs de vérifier qu'une portion du code mobile provient bien de vous.  
  
-   Par défaut, les bibliothèques partagées avec nom fort de [niveau 1](../../../docs/framework/misc/security-transparent-code-level-1.md) effectuent automatiquement une [LinkDemand](../../../docs/framework/misc/link-demands.md) implicite de confiance totale, sans que le créateur de la bibliothèque n'ait à faire quoi que ce soit.  
  
-   Si un appelant ne dispose pas d'une confiance totale et tente d'appeler ce type de bibliothèque, le runtime lève une <xref:System.Security.SecurityException> et l'appelant n'est pas autorisé à se connecter à la bibliothèque.  
  
-   Pour désactiver la **LinkDemand** automatique et empêcher la levée de l'exception, vous pouvez placer l'attribut **AllowPartiallyTrustedCallersAttribute** dans la portée de l'assembly d'une bibliothèque partagée. Cet attribut permet à vos bibliothèques d'être appelées depuis du code managé partiellement fiable.  
  
-   Le code partiellement fiable qui reçoit l'accès à une bibliothèque possédant cet attribut est toujours soumis à des restrictions supplémentaires définies par <xref:System.AppDomain>.  
  
-   Il n'est pas possible pour du code partiellement fiable d'appeler par programmation une bibliothèque qui ne possède pas l'attribut **AllowPartiallyTrustedCallersAttribute**.  
  
 Les bibliothèques qui sont réservées à une application particulière ne nécessitent pas de nom fort ni d'attribut **AllowPartiallyTrustedCallersAttribute**, et ne peuvent pas être référencées par du code potentiellement malveillant à l'extérieur de l'application. Ce code est protégé contre toute mauvaise utilisation, intentionnelle ou non, par du code mobile partiellement fiable, sans que le développeur n'ait à intervenir.  
  
 Vous devez envisager d'activer explicitement l'utilisation des types de code suivants pour le code partiellement fiable :  
  
-   Le code qui a été soigneusement testé à la recherche de vulnérabilités de sécurité et qui est conforme aux indications décrites dans [Instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md).  
  
-   Les bibliothèques de code avec nom fort qui sont écrites spécifiquement pour les scénarios de confiance partielle.  
  
-   Tous les composants \(partiellement ou entièrement fiables\) signés avec un nom fort qui seront appelés par du code téléchargé depuis Internet.  
  
> [!NOTE]
>  Certaines classes de la bibliothèque de classes .NET Framework ne possèdent pas l'attribut **AllowPartiallyTrustedCallersAttribute** et ne peuvent pas être appelées par du code partiellement fiable.  
  
## Voir aussi  
 [Sécurité d'accès du code](../../../docs/framework/misc/code-access-security.md)