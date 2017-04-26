---
title: "Modification du runtime dans le .NET Framework 4.7 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes,.NET Framework
- runtime changes,.NET Framework 4.7
- application compatibility
ms.assetid: 268eb334-7906-4e0b-a1e3-c74b745de2a5
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 321ec8f8293afad0f3da7fb6f907f45d404394cc
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-47"></a>Modifications du runtime dans le .NET Framework 4.7

Dans de rares cas, les modifications du runtime peuvent affecter les applications existantes qui ciblent les versions antérieures du .NET Framework mais qui s'exécutent sur une version ultérieure du runtime du .NET Framework. Elles incluent également des différences de comportement entre les applications qui s'exécutent sur différents environnements du runtime du .NET Framework. .NET Framework 4.6.2 apporte des modifications dans les domaines suivants :

- [Windows Presentation Foundation (WPF)](#WPF)

La colonne Portée des tableaux suivants indique l'importance de chaque modification :

- Majeur. Modification importante qui affecte un grand nombre d'applications ou qui nécessite de modifier significativement le code. Notez qu'aucune des modifications de reciblage ne correspond à cette catégorie.

- Mineur. Modification qui affecte un petit nombre d'applications ou qui nécessite peu de modifications du code.

- Limité. Modification qui affecte des applications dans des scénarios très spécifiques qui ne sont pas courants.

- Transparent. Modification qui n'a pas d'effet visible pour le développeur ou l'utilisateur de l'application. L'application n'a pas besoin d'être modifiée en raison de cette modification.

## <a name="a-namewpf--windows-presentation-foundation-wpf"></a><a name="WPF" /> Windows Presentation Foundation (WPF)

assetId:///M:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView(System.Int32)?qualifyHint=False&autoUpgrade=True

| Fonctionnalité | Modification | Impact | Portée |
|---|---|---|---|
| Méthode <xref:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView%2A> | Dans .NET Framework 4.6.2, la méthode <xref:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView%2A> s’exécute de façon asynchrone lorsque la virtualisation des colonnes est activée, mais que les largeurs de colonne n’ont pas été déterminées. Si les colonnes sont supprimées avant la fin de l’opération asynchrone, une <xref:System.ArgumentOutOfRangeException> peut se produire.<br/></br>À compter du 4.7 de .NET Framework 4.7, l’exception n’est plus levée dans ce scénario. | Cette modification améliore la fiabilité de la méthode. | Limité | 
|Arrière-plan <xref:System.Windows.Controls.Ribbon.RibbonGroup> | Dans .NET Framework 4.6.2 et versions antérieures, l’arrière-plan <xref:System.Windows.Controls.Ribbon.RibbonGroup> sur les versions localisées a été peint avec un pinceau transparent, ce qui entraîne une mauvaise expérience avec l’interface utilisateur. Dans le .NET Framework 4.7, WPF met à jour les ressources localisées pour le contrôle <xref:System.Windows.Controls.Ribbon.RibbonGroup>, ce qui garantit que le bon pinceau est sélectionné. | Pour tirer parti du nouveau comportement, mettez à niveau vers .NET Framework 4.7. | Limité |
| Vérificateur WPF | À compter de .NET Framework 4.6.1, le vérificateur orthographique dans les applications WPF lève parfois une <xref:System.ObjectDisposedException> lors de l’arrêt de l’application. <br/><br/>Dans .NET Framework 4.7, l’exception est gérée correctement par le runtime, garantissant ainsi que les applications ne sont pas affectées négativement. Il convient de noter que des exceptions de première chance occasionnelles continuent à être observées dans les applications en cours d’exécution sous un débogueur.  | Pour tirer parti du nouveau comportement, mettez à niveau vers .NET Framework 4.7.   | Limité |

## <a name="see-also"></a>Voir aussi

[Compatibilité d'applications dans le .NET Framework 4.7](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-7.md)


