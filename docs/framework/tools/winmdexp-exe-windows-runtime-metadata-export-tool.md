---
title: "Winmdexp.exe (Windows Runtime Metadata Export Tool) | Microsoft Docs"
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
  - "Windows Runtime Metadata Export Tool"
  - "Winmdexp.exe"
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Winmdexp.exe (Windows Runtime Metadata Export Tool)
L'outil Metadata Export [!INCLUDE[wrt](../../../includes/wrt-md.md)] \(Winmdexp.exe\) transforme un module .NET Framework en un fichier qui contient des métadonnées [!INCLUDE[wrt](../../../includes/wrt-md.md)].  Bien que les assemblys .NET Framework et les fichiers de métadonnées [!INCLUDE[wrt](../../../includes/wrt-md.md)] utilisent le même format physique, il y a des différences dans le contenu des tables de métadonnées. Autrement dit, les assemblys .NET Framework ne sont pas utilisables automatiquement comme composants [!INCLUDE[wrt](../../../includes/wrt-md.md)].  Le processus visant à transformer un module .NET Framework en un composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] est connu comme *exportation*.  Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] et [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], le fichier de métadonnées Windows \(.winmd\) résultant contient à la fois les métadonnées et l'implémentation.  
  
 Lorsque vous utilisez le modèle **[!INCLUDE[wrt](../../../includes/wrt-md.md)] Composant**, qui se situe dans le **Windows Store** pour C\# et Visual Basic dans [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] ou [!INCLUDE[vs_dev11_ext](../../../includes/vs-dev11-ext-md.md)], la cible du compilateur est un fichier .winmdobj et une étape de build suivante appelle Winmdexp.exe pour exporter le fichier .winmdobj vers un fichier .winmd.  C'est la méthode recommandée pour générer un composant [!INCLUDE[wrt](../../../includes/wrt-md.md)].  Utilisez Winmdexp.exe directement lorsque vous voulez contrôler davantage le processus de génération que Visual Studio le permet.  
  
 Cet outil est installé automatiquement avec Visual Studio.  Pour exécuter l'outil, utilisez l'invite de commandes développeur \(ou l'invite de commandes Visual Studio dans Windows 7\).  Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 À l'invite de commandes, tapez le texte suivant :  
  
## Syntaxe  
  
```  
  
winmdexp [options] winmdmodule  
```  
  
#### Paramètres  
  
|Argument ou option|Description|  
|------------------------|-----------------|  
|`winmdmodule`|Spécifie le module \(.winmdobj\) à exporter.  Un seul module est autorisé.  Pour créer ce module, utilisez l'option de compilateur `/target` avec la cible `winmdobj`.  Consultez [\/target:winmdobj \(Créer un fichier intermédiaire pour Windows Runtime\)](../Topic/-target:winmdobj%20\(C%23%20Compiler%20Options\).md) ou [\/target](../Topic/-target%20\(Visual%20Basic\).md) dans la bibliothèque MSDN.|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|Spécifie le fichier de documentation XML de sortie que Winmdexp.exe produira.  Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], le fichier de sortie est essentiellement identique au fichier de documentation XML d'entrée.|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|Spécifie le nom du fichier de documentation XML que le compilateur a produit avec `winmdmodule`.|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|Indique le nom du fichier de la base de données du programme \(PDB\) qui contient les symboles pour `winmdmodule`.|  
|`/nowarn:` `warning`|Supprime le nombre d'avertissements indiqué.  Pour *warning*, indiquez uniquement la partie numérique du code d'erreur, sans zéro significatif.|  
|`/out:` `file`<br /><br /> `/o:` `file`|Indique le nom du fichier de métadonnées Windows \(.winmd\) de sortie.|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|Spécifie le nom du fichier de la base de données du programme \(PDB\) de sortie qui contiendra les symboles pour le fichier de métadonnées Windows \(.winmd\) exporté.|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|Indique un fichier de métadonnées \(.winmd ou assembly\) à référencer lors de l'exportation.  Si vous utilisez des assemblys de référence dans "\\Program files \(x86\)\\Reference Assemblies\\Microsoft\\Framework\\.NETCore\\v4.5" \("\\Program Files\\..." sur les ordinateurs 32 bits\), incluez à la fois les références à System.Runtime.dll et mscorlib.dll.|  
|`/utf8output`|Spécifie que les messages de sortie utilisent un encodage en UTF\-8.|  
|`/warnaserror+`|Spécifie que tous les avertissements doivent être traités comme des erreurs.|  
|**@** `responsefile`|Spécifie un fichier de réponse \(.rsp\) qui contient des options \(et éventuellement `winmdmodule`\).  Chaque ligne dans `responsefile` doit contenir un seul argument ou une seule option.|  
  
## Notes  
 Winmdexp.exe n'est pas conçu pour convertir un assembly. NET Framework arbitraire en un fichier .winmd.  Il requiert un module compilé avec l'option `/target:winmdobj`, et des restrictions supplémentaires s'appliquent.  La plus importante de ces restrictions est que tous les types qui sont exposés dans la surface API de l'assembly doivent être de type [!INCLUDE[wrt](../../../includes/wrt-md.md)].  Pour plus d'informations, consultez la section "Déclaration de types dans les composants Windows Runtime" de l'article [Création de composants Windows Runtime en C\# et Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=238313) dans le centre de développement Windows.  
  
 Lorsque vous écrivez une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou un composant [!INCLUDE[wrt](../../../includes/wrt-md.md)] avec C\# ou Visual Basic, .NET Framework fournit le support pour effectuer la programmation avec [!INCLUDE[wrt](../../../includes/wrt-md.md)] de manière plus naturelle.  Pour cela, se référer à l'article [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).  Dans le processus, certains types de [!INCLUDE[wrt](../../../includes/wrt-md.md)] utilisés couramment sont mappés en types .NET Framework.  Winmdexp.exe inverse ce processus et produit une surface API qui utilise les types [!INCLUDE[wrt](../../../includes/wrt-md.md)] correspondants.  Par exemple, les types qui sont générés à partir du mappage de l'interface <xref:System.Collections.Generic.IList%601> aux types qui sont générés à partir de l'interface [!INCLUDE[wrt](../../../includes/wrt-md.md)] [IVector\<T\>](http://go.microsoft.com/fwlink/p/?LinkId=251132).  
  
## Voir aussi  
 [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)   
 [Création de composants Windows Runtime en C\# et Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=238313)   
 [Winmdexp.exe Error Messages](../../../docs/framework/tools/winmdexp-exe-error-messages.md)   
 [Build, Deployment, and Configuration Tools \(.NET Framework\)](http://msdn.microsoft.com/fr-fr/b8c921be-6012-4181-b8d4-ab15813fc9a7)