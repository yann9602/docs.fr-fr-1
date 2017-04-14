---
title: "Affichage des caract&#232;res asiatiques avec la propri&#233;t&#233; ImeMode | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "langues asiatiques"
  - "langues asiatiques, afficher avec IMEMode"
  - "caractères chinois, afficher avec IMEMode"
  - "globalisation (Windows Forms), jeux de caractères"
  - "mode IME"
  - "IMEMode (propriété)"
  - "Éditeur de méthode d'entrée (IME), mode"
  - "applications internationales (Windows Forms), affichage des caractères"
  - "caractères internationaux"
  - "caractères japonais, afficher avec IMEMode"
  - "caractères coréens"
  - "localisation (Windows Forms), jeux de caractères"
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Affichage des caract&#232;res asiatiques avec la propri&#233;t&#233; ImeMode
La propriété <xref:System.Windows.Forms.Control.ImeMode%2A> est utilisée par les formulaires et les contrôles pour forcer l'emploi d'un mode spécifique pour un éditeur de méthode d'entrée \(IME, Input Method Editor\).  L'IME est un composant essentiel pour écrire des scripts chinois, japonais et coréens, puisque ces systèmes d'écriture possèdent plus de caractères qu'il n'est possible d'en encoder sur un clavier ordinaire.  Par exemple, il est possible d'autoriser uniquement les caractères ASCII dans une zone de texte particulière.  Dans ce cas, vous pouvez affecter la valeur <xref:System.Windows.Forms.ImeMode> à la propriété <xref:System.Windows.Forms.Control.ImeMode%2A>. Les utilisateurs ne pourront alors entrer que des caractères ASCII dans cette zone de texte.  La valeur par défaut de la propriété <xref:System.Windows.Forms.Control.ImeMode%2A> est <xref:System.Windows.Forms.ImeMode>, par conséquent, si vous définissez la propriété pour un formulaire, tous les contrôles sur le formulaire héritent ce paramètre.  Pour plus d'informations, consultez [Control.ImeMode, propriété](frlrfSystemWindowsFormsControlClassImeModeTopic) et [ImeMode, énumération](frlrfSystemWindowsFormsImeModeClassTopic).  
  
## Voir aussi  
 [Globalisation des Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)