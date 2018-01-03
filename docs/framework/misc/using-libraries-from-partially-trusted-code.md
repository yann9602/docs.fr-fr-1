---
title: "Utilisation de bibliothèques à partir de code d'un niveau de confiance partiel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00f532e4e93936dbd719f2b8a0c060e54e16425b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-libraries-from-partially-trusted-code"></a>Utilisation de bibliothèques à partir de code d'un niveau de confiance partiel
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  Cette rubrique aborde le comportement des assemblys avec nom fort et s’applique uniquement aux [niveau 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblys. [Code Transparent de sécurité, niveau 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblys dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ou version ultérieure ne sont pas affectés par les noms forts. Pour plus d’informations sur les modifications apportées au système de sécurité, consultez [modifications de sécurité](../../../docs/framework/security/security-changes.md).  
  
 Les applications qui reçoivent moins de confiance totale de leur hôte ou d’un bac à sable ne sont pas autorisées à appeler partagée des bibliothèques managées, sauf si le créateur de la bibliothèque les autorise explicitement à l’aide de la <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut. Par conséquent, les auteurs d'applications doivent être conscients que certaines bibliothèques pas seront disponibles dans un contexte de confiance partielle. Par défaut, tout le code qui s’exécute dans un niveau de confiance partiel [sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) et n’est pas dans la liste des assemblys de confiance totale est partiellement approuvée. S'il n'est pas prévu que votre code soit exécuté dans un contexte de confiance partielle ou qu'il soit appelé par du code partiellement fiable, les informations de cette section ne vous concernent pas. Toutefois, si vous écrivez du code qui doit interagir avec du code partiellement fiable ou fonctionner dans un contexte de confiance partiel, vous devez prendre en compte les éléments suivants :  
  
-   Les bibliothèques doivent être signées avec un nom fort pour pouvoir être partagées par plusieurs applications. Les noms forts permettent à votre code d'être placé dans un Global Assembly Cache ou d'être ajouté à la liste de confiance totale d'un bac à sable <xref:System.AppDomain>. De plus, ils permettent aux utilisateurs de vérifier qu'une portion du code mobile provient bien de vous.  
  
-   Par défaut, fort [niveau 1](../../../docs/framework/misc/security-transparent-code-level-1.md) les bibliothèques partagées effectuent implicite [LinkDemand](../../../docs/framework/misc/link-demands.md) de confiance totale automatiquement, sans que le créateur de la bibliothèque n’ait à faire quoi que ce soit.  
  
-   Si un appelant ne dispose pas d'une confiance totale et tente d'appeler ce type de bibliothèque, le runtime lève une <xref:System.Security.SecurityException> et l'appelant n'est pas autorisé à se connecter à la bibliothèque.  
  
-   Pour désactiver cette **LinkDemand** et empêcher l’exception levée, vous pouvez placer le **AllowPartiallyTrustedCallersAttribute** attribut sur la portée de l’assembly d’un élément partagé bibliothèque. Cet attribut permet à vos bibliothèques d'être appelées depuis du code managé partiellement fiable.  
  
-   Le code partiellement fiable qui reçoit l'accès à une bibliothèque possédant cet attribut est toujours soumis à des restrictions supplémentaires définies par <xref:System.AppDomain>.  
  
-   Il n’existe aucun moyen de programmation pour le code partiellement fiable d’appeler une bibliothèque qui n’a pas la **AllowPartiallyTrustedCallersAttribute** attribut.  
  
 Bibliothèques qui sont réservées à une application particulière ne nécessitent pas un nom fort ou **AllowPartiallyTrustedCallersAttribute** d’attribut et ne peut pas être référencées par du code potentiellement malveillant à l’extérieur de l’application. Ce code est protégé contre toute mauvaise utilisation, intentionnelle ou non, par du code mobile partiellement fiable, sans que le développeur n'ait à intervenir.  
  
 Vous devez envisager d'activer explicitement l'utilisation des types de code suivants pour le code partiellement fiable :  
  
-   Code qui a été soigneusement testé des failles de sécurité et est conforme aux indications décrites dans [instructions de codage sécurisé](../../../docs/standard/security/secure-coding-guidelines.md).  
  
-   Les bibliothèques de code avec nom fort qui sont écrites spécifiquement pour les scénarios de confiance partielle.  
  
-   Tous les composants (partiellement ou entièrement fiables) signés avec un nom fort qui seront appelés par du code téléchargé depuis Internet.  
  
> [!NOTE]
>  Certaines classes dans la bibliothèque de classes .NET Framework ne possèdent pas la **AllowPartiallyTrustedCallersAttribute** d’attribut et ne peut pas être appelé par du code partiellement fiable.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité d’accès du code](../../../docs/framework/misc/code-access-security.md)
