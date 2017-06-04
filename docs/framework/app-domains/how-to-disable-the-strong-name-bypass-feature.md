---
title: "Comment&#160;: d&#233;sactiver la fonctionnalit&#233; consistant &#224; ignorer les noms forts | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fonctionnalité consistant à ignorer les noms forts"
  - "assemblys avec nom fort, charger dans des domaines d’application de confiance"
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
caps.latest.revision: 30
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 30
---
# Comment&#160;: d&#233;sactiver la fonctionnalit&#233; consistant &#224; ignorer les noms forts
À partir du .NET Framework version 3.5 Service Pack 1 \(SP1\), les signatures de nom fort ne sont pas validées lorsqu'un assembly est chargé dans un objet <xref:System.AppDomain> de confiance totale, tel que le <xref:System.AppDomain> par défaut de la zone `MyComputer`.  Cette fonctionnalité permet d'ignorer les noms forts.  Dans un environnement de confiance totale, les demandes de <xref:System.Security.Permissions.StrongNameIdentityPermission> aboutissent toujours pour les assemblys de confiance totale signés, quelle que soit leur signature.  La seule restriction est que l'assembly doit présenter un niveau de confiance suffisant, étant donné que c'est le cas de sa zone.  Puisque le nom fort n'est pas un facteur déterminant dans ces conditions, aucune validation n'est requise.  Lorsque la validation des signatures de nom fort est ignorée, les performances sont considérablement améliorées.  
  
 La fonctionnalité consistant à ignorer les noms forts s'applique à tous les assemblys de confiance totale dont la signature n'est pas différée et qui sont chargés dans un <xref:System.AppDomain> de confiance totale à partir du répertoire spécifié par leur propriété <xref:System.AppDomainSetup.ApplicationBase%2A>.  
  
 Vous pouvez remplacer cette fonctionnalité pour toutes les applications ouvertes sur un ordinateur en définissant une valeur de clé de Registre.  Vous pouvez remplacer la définition d'une application à l'aide du fichier de configuration de l'application.  Vous ne pouvez pas rétablir la fonctionnalité consistant à ignorer les noms forts pour une application si elle a été désactivée par le biais de la clé de Registre.  
  
 Lorsque vous remplacez la fonctionnalité consistant à ignorer les noms forts, seule l'exactitude du nom fort est validée. Aucune recherche de <xref:System.Security.Permissions.StrongNameIdentityPermission> n'est effectuée.  Si vous souhaitez confirmer un nom fort spécifique, vous devez effectuer un contrôle distinct.  
  
> [!IMPORTANT]
>  La possibilité de forcer la validation d'un nom fort dépend d'une clé de Registre, comme décrit dans la procédure suivante.  Si une application s'exécute sous un compte ne disposant pas de l'autorisation de liste de contrôle d'accès \(ACL\) pour accéder à la clé de Registre, le paramètre n'est pas effectif.  Vous devez vous assurer que les droits ACL sont configurés pour cette clé et qu'elle peut ainsi être lue pour tous les assemblys.  
  
### Pour désactiver la fonctionnalité consistant à ignorer les noms forts pour toutes les applications  
  
-   Sur les ordinateurs 32 bits, dans la base de registres, créez une entrée DWORD avec une valeur de 0 nommée `AllowStrongNameBypass` sous la clé HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ .NETFramework.  
  
-   Sur les ordinateurs 64 bits, dans la base de registres, créez une entrée DWORD avec une valeur de 0 nommée `AllowStrongNameBypass` sous les clés HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework et HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework.  
  
### Pour désactiver la fonctionnalité consistant à ignorer les noms forts pour une application  
  
1.  Ouvrez ou créez le fichier de configuration de l'application.  
  
     Pour plus d'informations sur ce fichier, consultez la section Fichiers de configuration des applications dans [Configuration d'applications](../../../docs/framework/configure-apps/index.md).  
  
2.  Ajoutez l'entrée suivante :  
  
    ```  
    <configuration>  
      <runtime>  
         < bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Vous pouvez rétablir la fonctionnalité en supprimant le paramètre du fichier de configuration ou en affectant à l'attribut la valeur « true ».  
  
> [!NOTE]
>  Vous ne pouvez activer et désactiver la validation de nom fort que si la fonctionnalité consistant à ignorer les noms forts est activée pour l'ordinateur.  Si cette fonctionnalité est désactivée, les noms forts sont validés pour toutes les applications et vous ne pouvez pas contourner la validation pour une application.  
  
## Voir aussi  
 [Sn.exe \(Strong Name Tool\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [\<bypassTrustedAppStrongNames\>, élément](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)   
 [Création et utilisation d'assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)