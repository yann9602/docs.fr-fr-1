---
title: "Packaging and Deploying Custom My Extensions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My namespace, customizing"
  - "My namespace"
  - "My namespace, extending"
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Packaging and Deploying Custom My Extensions (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Basic vous permet de déployer facilement les extensions de votre espace de noms `My` personnalisé en utilisant des modèles Visual Studio.  Si vous créez un modèle de projet pour lequel vos extensions `My` font partie intégrante du nouveau type de projet, vous pouvez simplement inclure votre code d'extension `My` personnalisé avec le projet lors de l'exportation du modèle.  Pour plus d'informations sur l'exportation des modèles de projet, consultez [Comment : créer des modèles de projet](../Topic/How%20to:%20Create%20Project%20Templates.md).  
  
 Si votre extension `My` personnalisée se trouve dans un seul fichier de code, vous pouvez exporter le fichier en tant que modèle d'élément que les utilisateurs peuvent ajouter à tout type de projet Visual Basic.  Vous pouvez ensuite personnaliser le modèle d'élément pour activer d'autres fonctions et comportements de votre extension `My` personnalisée dans un projet Visual Basic.  Il s'agit notamment des suivantes :  
  
-   Permettre aux utilisateurs de gérer votre extension `My` personnalisée à partir de la page **Extensions My** du Concepteur de projets de Visual Basic.  
  
-   Ajouter automatiquement votre extension `My` personnalisée lorsqu'une référence à un assembly donné est ajoutée à un projet.  
  
-   Masquer le modèle d'élément de l'extension `My` dans la boîte de dialogue **Ajouter un élément** afin qu'il ne soit pas inclus dans la liste d'éléments du projet.  
  
 Cette rubrique explique comment empaqueter une extension `My` personnalisée en tant que modèle d'élément caché pouvant être géré à partir de la page **Extensions My** du Concepteur de projets de Visual Basic.  L'extension `My` personnalisée peut également être ajoutée automatiquement lorsqu'une référence à un assembly spécifié est ajoutée à un projet.  
  
## Créer une extension de l'espace de noms My  
 La première étape de création d'un package de déploiement pour une extension `My` personnalisée consiste à créer l'extension comme un fichier de code unique.  Pour plus de détails et d'aide sur la création d'une extension `My` personnalisée, consultez [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).  
  
## Exporter une extension de l'espace de noms My comme un modèle d'élément  
 Après avoir obtenu un fichier de code qui inclut votre extension de l'espace de noms `My`, vous pouvez exporter le fichier de code en tant que modèle d'élément Visual Studio.  Pour plus d'instructions sur l'exportation d'un fichier en tant que modèle d'élément Visual Studio, consultez [Comment : créer des modèles d'élément](../Topic/How%20to:%20Create%20Item%20Templates.md).  
  
> [!NOTE]
>  Si votre extension de l'espace de noms `My` a une dépendance sur un assembly donné, vous pouvez personnaliser votre modèle d'élément pour installer automatiquement votre extension lors de l'ajout d'une référence à cet assembly.  Par conséquent, vous pouvez exclure la référence de cet assembly lors de l'exportation du fichier de code en tant que modèle d'élément Visual Studio.  
  
## Personnaliser le modèle d'élément  
 Vous pouvez autoriser la gestion de votre modèle d'élément à partir de la page **Extensions My** du Concepteur de projets de Visual Basic.  Vous pouvez également autoriser l'ajout automatique du modèle d'élément lorsqu'une référence à un assembly donné est ajoutée à un projet.  Pour activer ces personnalisations, ajoutez un nouveau fichier nommé CustomData à votre modèle, puis ajoutez un nouvel élément au XML dans votre fichier .vstemplate.  
  
### Ajouter le fichier CustomData  
 Le fichier CustomData est un fichier texte qui porte l'extension .CustomData \(le nom de fichier peut prendre toute valeur pertinente pour votre modèle\) et contient le XML.  Le XML du fichier CustomData demande à Visual Basic d'inclure votre extension `My` lors de l'utilisation de la page **Extensions My** du Concepteur de projets de Visual Basic.  Vous pouvez éventuellement ajouter l'attribut \<`AssemblyFullName>` à votre fichier XML CustomData.  Cette option indique à Visual Basic d'installer automatiquement votre extension `My` personnalisée lorsqu'une référence à un assembly donné est ajoutée au projet.  Vous pouvez utiliser un éditeur de texte ou un éditeur XML pour créer le fichier CustomData, puis l'ajouter au dossier compressé \(fichier .zip\) de votre modèle d'élément.  
  
 Par exemple, le XML suivant affiche le contenu d'un fichier CustomData qui ajoute l'élément de modèle au dossier Extensions My d'un projet Visual Basic lorsqu'une référence à l'assembly Microsoft.VisualBasic.PowerPacks.Vs.dll est ajoutée au projet.  
  
```  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 Le fichier CustomData contient un élément \<`VBMyExtensionTemplate>` qui dispose des attributs répertoriés dans le tableau suivant.  
  
|||  
|-|-|  
|Attribut|Description|  
|`ID`|Obligatoire.  Identificateur unique pour l'extension.  Si l'extension qui possède cet ID a déjà été ajoutée au projet, l'utilisateur ne sera pas invité à l'ajouter à nouveau.|  
|`Version`|Obligatoire.  Numéro de version du modèle d'élément.|  
|`AssemblyFullName`|Facultatif.  Nom de l'assembly  Lorsqu'une référence à cet assembly est ajoutée au projet, l'utilisateur est invité à ajouter l'extension `My` de ce modèle d'élément.|  
  
### Ajouter l'élément \<CustomDataSignature\> au fichier .vstemplate  
 Pour identifier votre modèle d'élément Visual Studio en tant qu'extension de l'espace de noms `My`, vous devez également modifier le fichier .vstemplate pour votre modèle d'élément.  Vous devez ajouter un élément `<CustomDataSignature>` à l'élément `<TemplateData>`.  L'élément `<CustomDataSignature>` doit contenir le texte `Microsoft.VisualBasic.MyExtension`, comme illustré dans l'exemple suivant.  
  
```  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 Vous ne pouvez pas modifier directement les fichiers d'un dossier compressé \(fichier .zip\).  Vous devez copier le fichier .vstemplate à partir du dossier compressé, le modifier, puis remplacer le fichier .vstemplate dans le dossier compressé par votre copie mise à jour.  
  
 L'exemple suivant affiche le contenu d'un fichier .vstemplate dont l'élément `<CustomDataSignature>` a été ajouté.  
  
```  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature       >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
  </TemplateData>  
  <TemplateContent>  
    <References />  
    <ProjectItem SubType="Code"   
                 TargetFileName="$fileinputname$.vb"  
                 ReplaceParameters="true"  
     >MyCustomExtensionModule.vb</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
```  
  
## Installer le modèle  
 Pour installer le modèle, vous pouvez copier le dossier compressé \(fichier .zip\) dans le dossier de modèles d'élément Visual Basic \(par exemple, Mes documents\\Visual Studio 2008\\Templates\\Item Templates\\Visual Basic\).  Vous pouvez également publier le modèle comme un fichier du programme d'installation de Visual Studio \(.vsi\).  Pour plus d'informations sur la publication de votre modèle en tant que fichier du programme d'installation de Visual Studio, consultez [NIB: How to: Publish Project Templates](http://msdn.microsoft.com/fr-fr/b9087f58-64e9-4767-bf54-e3bf40d63b20).  
  
## Voir aussi  
 [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)   
 [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Extensions My, page du Concepteur de projets](/visual-studio/ide/reference/my-extensions-page-project-designer-visual-basic)