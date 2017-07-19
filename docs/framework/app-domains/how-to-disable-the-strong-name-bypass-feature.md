---
title: "Guide pratique pour désactiver la fonctionnalité consistant à ignorer les noms forts | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
caps.latest.revision: 30
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 73e27a6a1cb58a410bf3c1601e5a5412762242c7
ms.contentlocale: fr-fr
ms.lasthandoff: 06/02/2017

---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Guide pratique pour désactiver la fonctionnalité consistant à ignorer les noms forts
À partir du .NET Framework version 3.5 Service Pack 1 (SP1), les signatures de noms forts ne sont pas validées quand un assembly est chargé dans un objet <xref:System.AppDomain> de confiance totale, tel que le <xref:System.AppDomain> par défaut pour la zone `MyComputer`. Cette fonctionnalité permet d’ignorer les noms forts. Dans un environnement de confiance totale, les demandes de <xref:System.Security.Permissions.StrongNameIdentityPermission> aboutissent toujours pour les assemblys de confiance totale signés, quelle que soit leur signature. La seule restriction est que l’assembly doit être entièrement fiable, car sa zone est entièrement fiable. Le nom fort n’étant pas un facteur déterminant dans ces conditions, il n’y a aucune raison pour qu’il soit validé. Ignorer la validation des signatures de noms forts fournit une amélioration significative des performances.  
  
 Cette fonctionnalité consistant à ignorer la validation s’applique à tout assembly de confiance totale qui n’est pas à signature différée et qui est chargé dans n’importe quel <xref:System.AppDomain> de confiance totale à partir du répertoire spécifié par sa propriété <xref:System.AppDomainSetup.ApplicationBase%2A>.  
  
 Vous pouvez outrepasser cette fonctionnalité pour toutes les applications sur un ordinateur en définissant une valeur de clé de Registre. Vous pouvez remplacer le paramètre pour une application unique en utilisant un fichier de configuration. Vous ne pouvez pas rétablir cette fonctionnalité pour une application si elle a été désactivée par la clé de Registre.  
  
 Quand vous outrepassez cette fonctionnalité, seule l’exactitude du nom fort est validée ; aucune vérification n’est effectuée pour <xref:System.Security.Permissions.StrongNameIdentityPermission>. Si vous souhaitez confirmer un nom fort spécifique, vous devez effectuer un contrôle distinct.  
  
> [!IMPORTANT]
>  La possibilité de forcer la validation des noms forts dépend d’une clé de Registre, comme décrit dans la procédure suivante. Si une application s’exécute sous un compte qui ne dispose pas de l’autorisation ACL (liste de contrôle d’accès) d’accès à cette clé de Registre, le paramètre est inefficace. Vous devez vérifier que les droits ACL sont configurés pour cette clé afin qu’elle puisse être lue pour tous les assemblys.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>Pour désactiver la fonctionnalité consistant à ignorer les noms forts pour toutes les applications  
  
-   Sur les ordinateurs 32 bits, dans le Registre système, créez une entrée DWORD avec la valeur 0 nommée `AllowStrongNameBypass` sous la clé HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework.  
  
-   Sur les ordinateurs 64 bits, dans le Registre système, créez une entrée DWORD avec la valeur 0 nommée `AllowStrongNameBypass` sous les clés HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework et HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>Pour désactiver la fonctionnalité consistant à ignorer les noms forts pour une seule application  
  
1.  Ouvrez ou créez le fichier de configuration de l’application.  
  
     Pour plus d’informations sur ce fichier, consultez la section Fichiers de configuration de l’application dans [Configuration des applications](../../../docs/framework/configure-apps/index.md).  
  
2.  Ajoutez l’entrée suivante :  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Vous pouvez restaurer la fonctionnalité pour l’application en supprimant le paramètre du fichier de configuration ou en affectant la valeur « true » à l’attribut.  
  
> [!NOTE]
>  Vous pouvez activer et désactiver la validation des noms forts pour une application uniquement si la fonctionnalité consistant à ignorer la validation est activée pour l’ordinateur. Si cette fonctionnalité a été désactivée pour l’ordinateur, les noms forts sont validés pour toutes les applications et vous ne pouvez pas ignorer la validation pour une application unique.  
  
## <a name="see-also"></a>Voir aussi  
 [Sn.exe (Outil Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [\<bypassTrustedAppStrongNames>, élément](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)   
 [Création et utilisation d’assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
