---
title: "Quelles sont les nouveautés dans .NET Standard"
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
ms.##devlang: dotnet
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e938c009b79af3b2f36094bbb74f4d38baeeac0b
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="whats-new-in-the-net-standard"></a>Quelles sont les nouveautés dans .NET Standard

.NET Standard est une spécification formelle qui définit un contrôle de version du jeu d’API qui doit être disponibles sur les implémentations de .NET qui sont conformes avec cette version de la norme. .NET Standard est destiné aux développeurs de bibliothèques. Une bibliothèque qui cible une version .NET Standard peut être utilisée sur toute implémentation du .NET Framework ou .NET Core Xamarin qui prend en charge cette version de la norme.

La version la plus récente de .NET Standard est 2.0. Il est inclus avec le Kit de développement logiciel .NET Core 2.0, ainsi qu’avec Visual Studio 2017 Version 15.3 avec la charge de travail .NET Core installé.

## <a name="supported-net-implementations"></a>Implémentations .NET pris en charge

La norme de .NET 2.0 est pris en charge par les implémentations .NET suivantes :

- .NET core 2.0
- .NET Framework 4.6.1
- Mono 5.4
- Xamarin.iOS 10.14
- Xamarin.Mac 3.8
- Xamarin.Android 8.0
- Universal Windows Platform 10.0.16299

## <a name="whats-new-in-the-net-standard-20"></a>Nouveautés de .NET 2.0 Standard
 
La norme de .NET 2.0 inclut les nouvelles fonctionnalités suivantes :

**Un jeu largement étendu d’API**

Jusqu'à la version 1.6, .NET Standard inclus un relativement petit sous-ensemble d’API. Parmi ceux exclus ont de nombreuses API ont été utilisés dans le .NET Framework ou Xamarin. Cela complique le développement, car elle requiert aux développeurs de trouver remplacements appropriés pour les API familier lorsqu’ils développent des applications et les bibliothèques qui ciblent plusieurs implémentations de .NET. La norme de .NET 2.0 résout cette limitation en ajoutant plus de 20 000 API plus que dans la version 1.6 .NET Standard, la version précédente de la norme. Pour obtenir la liste des API qui ont été ajoutés à la norme de .NET 2.0, consultez [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md). 

Certains des ajouts à la <xref:System> inclure de l’espace de noms Standard de .NET 2.0 :

- Prise en charge pour la <xref:System.AppDomain> classe.
- Meilleure prise en charge pour l’utilisation des groupes de membres supplémentaires dans la <xref:System.Array> classe.
- Meilleure prise en charge pour l’utilisation des attributs de membres supplémentaires dans la <xref:System.Attribute> classe.
- Calendrier mieux la prise en charge et les options de mise en forme supplémentaires pour <xref:System.DateTime> valeurs.
- Supplémentaires <xref:System.Decimal> arrondi des fonctionnalités.
- Des fonctionnalités supplémentaires dans la <xref:System.Environment> classe.
- Meilleur contrôle sur le garbage collector via la <xref:System.GC> classe.
- Meilleure prise en charge pour la comparaison de chaînes, énumération et la normalisation dans la <xref:System.String> classe.
- Prise en charge de l’heure d’été réglages et les temps de transition dans le <xref:System.TimeZoneInfo.AdjustmentRule> et <xref:System.TimeZoneInfo.TransitionTime> classes.
- Considérablement améliorée des fonctionnalités dans le <xref:System.Type> classe.
- Meilleure prise en charge pour la désérialisation des objets d’exception en ajoutant un constructeur d’exception avec <xref:System.Runtime.Serialization.SerializationInfo> et <xref:System.Runtime.Serialization.StreamingContext> paramètres.

**Prise en charge pour les bibliothèques .NET Framework**

La grande majorité des bibliothèques de cibler le .NET Framework plutôt que .NET Standard. Toutefois, la plupart des appels dans ces bibliothèques est les API qui sont incluses dans la norme de .NET 2.0. À compter de la norme de .NET 2.0, vous pouvez accéder à des bibliothèques de .NET Framework à partir d’une bibliothèque .NET Standard à l’aide un [shim de compatibilité](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification). Cette couche de compatibilité est transparente pour les développeurs ; vous n’avez rien à faire pour tirer parti des bibliothèques .NET Framework.

La seule exigence est que les API appelées par la bibliothèque de classes .NET Framework doivent être inclus dans la norme de .NET 2.0.

**Prise en charge de Visual Basic**

Vous pouvez maintenant développer les bibliothèques .NET Standard dans Visual Basic. Pour les développeurs Visual Basic à l’aide de Visual Studio 2017 Version 15.3 ou version ultérieure avec la charge de travail .NET Core installé, Visual Studio inclut désormais un modèle de bibliothèque de classes .NET Standard. Pour les développeurs Visual Basic qui utilisent d’autres outils de développement et les environnements, vous pouvez utiliser la [dotnet nouvelle](../../core/tools/dotnet-new.md) commande pour créer un projet de bibliothèque Standard de .NET. Pour plus d’informations, consultez la [prise en charge pour les bibliothèques .NET Standard pour les outils](#tooling).

<a name="tooling" />**Prise en charge des outils pour les bibliothèques .NET Standard**

Avec la version de .NET Core 2.0 et .NET Standard 2.0, les deux 2017 Studio Visual et [.NET Core Interface de ligne de commande (CLI)](../../core/tools/index.md) incluent des outils de prise en charge pour la création de bibliothèques .NET Standard. 

Si vous installez Visual Studio avec le **.NET Core le développement multiplateforme** charge de travail, vous pouvez créer un projet de bibliothèque Standard de .NET 2.0 à l’aide d’un modèle de projet, comme le montre l’illustration suivante. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Ajouter le projet de bibliothèque de nouveau .NET Standard](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![Ajouter le projet de bibliothèque de nouveau .NET Standard](./media/std-project-vb.png)
---

Si vous utilisez l’interface .NET Core CLI, ce qui suit [dotnet nouvelle](../../core/tools/dotnet-new.md) commande crée un projet de bibliothèque de classes qui cible .NET Standard 2.0.

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a>Voir aussi
[.NET standard](../net-standard.md)
[présentation .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
