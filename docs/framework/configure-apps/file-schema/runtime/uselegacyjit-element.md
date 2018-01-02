---
title: "&lt;useLegacyJit&gt; élément"
ms.custom: 
ms.date: 04/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d2a71e44db2d6e85ae730f4603bf191f54525c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltuselegacyjitgt-element"></a>&lt;useLegacyJit&gt; élément

Détermine si le common language runtime utilise le compilateur JIT 64 bits hérité pour la compilation juste-à-temps.  
  
\<configuration>  
\<runtime >  
\<useLegacyJit >
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<useLegacyJit enabled=0|1 />
```

Nom de l’élément `useLegacyJit` respecte la casse.
  
## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
| Attribut | Description                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Attribut requis.<br><br>Spécifie si le runtime utilise le compilateur JIT 64 bits hérité. |  
  
### <a name="enabled-attribute"></a>attribut Enabled  
  
| Value | Description                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Le common language runtime utilise le nouveau compilateur JIT 64 bits inclus dans le .NET Framework 4.6 et versions ultérieures. |  
| 1     | Le common language runtime utilise le compilateur JIT 64 bits plus anciens.                                                     |  
  
### <a name="child-elements"></a>Éléments enfants

Aucun.
  
### <a name="parent-elements"></a>Éléments parents  
  
| Élément         | Description                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework. |  
| `runtime`       | Contient des informations sur les options d'initialisation du runtime.                                                        |  
  
## <a name="remarks"></a>Notes  

À compter de .NET Framework 4.6, le common language runtime utilise un nouveau compilateur 64 bits pour la compilation juste à temps (JIT) par défaut. Dans certains cas, cela peut entraîner une différence de comportement du code d’application qui a été compilé juste-à la version précédente du compilateur JIT 64 bits. En définissant le `enabled` attribut de la `<useLegacyJit>` élément `1`, vous pouvez désactiver le nouveau compilateur JIT 64 bits et à la place compiler votre application à l’aide du compilateur JIT 64 bits hérité.  
  
> [!NOTE]
> Le `<useLegacyJit>` élément affecte uniquement la compilation JIT 64 bits. Compilation avec le compilateur JIT 32 bits n’est pas affectée.  
  
Au lieu d’utiliser une fichier de configuration, vous pouvez activer le compilateur JIT 64 bits hérité de deux manières différentes :  
  
- Définition d’une variable d’environnement

  Définir le `COMPLUS_useLegacyJit` variable d’environnement soit `0` (utiliser le nouveau compilateur JIT 64 bits) ou `1` (utiliser le compilateur JIT 64 bits plus anciens) :
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  La variable d’environnement a *étendue globale*, ce qui signifie qu’il affecte toutes les applications s’exécutent sur l’ordinateur. Si la valeur, elle peut être substituée par le paramètre fichier de configuration. Le nom de variable d’environnement ne respecte pas la casse.
  
- Ajout d’une clé de Registre

  Vous pouvez activer le compilateur JIT 64 bits hérité en ajoutant un `REG_DWORD` valeur soit la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` ou `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` clé dans le Registre. La valeur est nommée `useLegacyJit`. Si la valeur est 0, le nouveau compilateur est utilisé. Si la valeur est 1, le compilateur JIT 64 bits hérité est activé. Le nom de la valeur du Registre n’est pas sensible à la casse.
  
  Ajout de la valeur pour le `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` clé affecte toutes les applications en cours d’exécution sur l’ordinateur. Ajout de la valeur pour le `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` clé affecte toutes les applications exécutées par l’utilisateur actuel. Si un ordinateur est configuré avec plusieurs comptes d’utilisateur, seules les applications exécutées par l’utilisateur actuel sont affectées, sauf si la valeur est ajoutée aux clés de Registre pour d’autres utilisateurs ainsi. Ajout de la `<useLegacyJit>` élément vers un fichier de configuration remplace les paramètres du Registre, s’ils sont présents.  
  
## <a name="example"></a>Exemple  

Le fichier de configuration suivant désactive la compilation avec le nouveau compilateur JIT 64 bits et utilise à la place le compilateur JIT 64 bits hérité.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

[\<runtime > élément](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)   
[\<configuration > élément](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)   
[Atténuation : nouveau compilateur JIT 64 bits](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
