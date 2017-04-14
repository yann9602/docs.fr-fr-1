---
title: "Noms d&#39;assemblys | Microsoft Docs"
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
  - "assemblys (.NET Framework), noms"
  - "noms (.NET Framework), assemblys"
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Noms d&#39;assemblys
Un nom d'assembly est stocké dans des métadonnées et a un impact significatif sur la portée de l'assembly et son utilisation par une application.  Un assembly avec nom fort possède un nom qualifié complet qui comprend son nom, sa culture, sa clé publique et son numéro de version.  Il est fréquemment désigné par le nom complet, et peut être obtenu, pour les assemblys chargés, à l'aide de la propriété <xref:System.Reflection.Assembly.FullName%2A>.  
  
 Le runtime utilise ces informations pour rechercher l'assembly et le distinguer des autres assemblys portant le même nom.  Par exemple, un assembly avec nom fort appelé `myTypes` peut avoir le nom qualifié complet suivant :  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  L'architecture de processeur est ajoutée à l'identité de l'assembly dans la version 2.0 du .NET Framework pour autoriser les versions spécifiques au processeur des assemblys.  Vous pouvez créer des versions d'assembly dont l'identité diffère uniquement par l'architecture de processeur, par exemple des versions spécifiques au processeur 32 bits et 64 bits.  L'architecture de processeur n'est pas obligatoire pour les noms forts.  Pour plus d'informations, consultez <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=fullName>.  
  
 Dans cet exemple, le nom qualifié complet indique que l'assembly `myTypes` possède un nom fort avec un jeton de clé publique, que sa valeur de culture est Anglais \(États\-Unis\) et son numéro de version 1.0.1234.0.  Son architecture de processeur est « msil », ce qui signifie qu'il sera compilé juste\-à\-temps \(JIT, just\-in\-time\) en code 32 bits ou 64 bits selon le système d'exploitation et le processeur.  
  
 Le code qui demande des types dans un assembly doit utiliser un nom d'assembly qualifié complet.  Il s'agit d'une liaison qualifiée complète.  La liaison partielle, qui ne spécifie qu'un nom d'assembly, n'est pas autorisée pour référencer les assemblys dans le .NET Framework.  
  
 Toutes les références à des assemblys constituant le .NET Framework doivent également contenir un nom qualifié complet de l'assembly.  Par exemple, la référence à l'assembly .NET Framework System.Data pour la version 1.0 serait la suivante :  
  
```  
  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
  
```  
  
 Notez que la version correspond au numéro de version de tous les assemblys .NET Framework fournis avec le .NET Framework version 1.0.  Pour les assemblys .NET Framework, la valeur de culture est toujours neutre et la clé publique est la même que celle présentée dans l'exemple ci\-dessus.  
  
 Par exemple, pour ajouter la référence d'un assembly à un fichier de configuration en vue de configurer un écouteur de trace, vous incluez le nom qualifié complet de l'assembly system .NET Framework :  
  
```  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  Lors de la liaison à un assembly, le runtime traite les noms d'assemblys comme ne respectant pas la casse, mais préserve la casse utilisée dans un nom d'assembly.  Plusieurs outils du [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] gèrent les noms d'assemblys comme respectant la casse.  Pour de meilleurs résultats, gérez les noms d'assemblys comme s'ils respectaient la casse.  
  
## Attribution d'un nom aux composants d'application  
 Le runtime ne tient pas compte du nom de fichier lors de la détermination de l'identité d'un assembly.  L'identité de l'assembly, qui est constituée du nom, de la version, de la culture et du nom fort de l'assembly, doit être claire pour le runtime.  
  
 Par exemple, si vous avez un assembly appelé myAssembly.exe qui fait référence à un assembly appelé myAssembly.dll, la liaison se produit correctement si vous exécutez myAssembly.exe.  Cependant, si une autre application exécute myAssembly.exe à l'aide de la méthode <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=fullName>, le runtime détermine que « myAssembly » est déjà chargé lorsque myAssembly.exe demande la création d'une liaison avec « myAssembly ». Dans ce cas, myAssembly.dll n'est jamais chargé.  Étant donné que myAssembly.exe ne contient pas le type demandé, une exception <xref:System.TypeLoadException> se produit.  
  
 Pour éviter ce problème, assurez\-vous que les assemblys composant votre application n'ont pas le même nom d'assembly ou placez les assemblys possédant le même nom dans des répertoires différents.  
  
> [!NOTE]
>  Si vous placez un assembly avec nom fort dans le Global Assembly Cache, le nom de fichier de l'assembly doit correspondre au nom de l'assembly \(sans l'extension du nom de fichier, par exemple .exe ou .dll\).  Par exemple, si le nom de fichier d'un assembly est myAssembly.dll, le nom de l'assembly doit être myAssembly.  Les assemblys privés déployés uniquement dans le répertoire racine de l'application peuvent avoir un nom d'assembly différent du fichier de fichier.  
  
## Voir aussi  
 [Comment : déterminer le nom qualifié complet d'un assembly](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)   
 [Création d'assemblys](../../../docs/framework/app-domains/create-assemblies.md)   
 [Assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md)   
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)   
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)