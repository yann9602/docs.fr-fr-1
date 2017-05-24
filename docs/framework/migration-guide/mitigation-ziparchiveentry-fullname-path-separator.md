---
title: "Atténuation : Séparateur de chemin ZipArchiveEntry.FullName | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 747c98e0fd9db95c52531b398aa33161decac294
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Atténuation : Séparateur de chemin ZipArchiveEntry.FullName
En commençant par les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], le séparateur de chemin d’accès utilisé dans la propriété <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=fullName> a été modifié de la barre oblique inverse (« \\ ») utilisée dans les versions antérieures de .NET Framework à la barre oblique (« / »).   Les objets <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=fullName> sont créés en appelant une des surcharges de la méthode <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=fullName>.  
  
## <a name="impact"></a>Impact  
 L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.  
  
 Décompresser un fichier zip créé par une application qui cible une version antérieure de .NET Framework sur les systèmes d’exploitation non Windows tels que les ordinateurs Macintosh ne permet pas de conserver la structure de répertoire. Par exemple, pour les ordinateurs Macintosh, cela crée un ensemble de fichiers dont le nom concatène le chemin d’accès, ainsi que toute barre oblique inverse (« \\ ») et le nom de fichier. Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.  
  
 L’impact de ce changement sur les fichiers .ZIP qui sont décompressés sur le système d’exploitation par les API dans de l’espace de noms <xref:System.IO> de .NET Framework doit être minimal, étant donné que ces API peuvent gérer en toute sans problème aussi bien une barre oblique (« / ») qu’une barre oblique inverse (« \\ ») comme séparateur de chemin d’accès.  
  
## <a name="mitigation"></a>Atténuation  
 Si ce comportement n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant un paramètre de configuration pour la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de votre application. L’exemple suivant montre la section `<runtime>` et l’option d’annulation.  
  
```  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 De plus, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sur le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ou ultérieur peuvent adhérer à ce comportement en ajoutant un paramètre de configuration dans la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application. L’exemple suivant montre la section `<runtime>` et l’option d’activation.  
  
```  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)   
 [Compatibilité des applications dans la version 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

