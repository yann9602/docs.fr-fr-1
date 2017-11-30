---
title: "Seedwork (classes de base réutilisables et interfaces pour votre modèle de domaine)"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Seedwork (classes de base réutilisables et interfaces pour votre modèle de domaine)"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 17602d94ea167997389a77f0d2358326258a8219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (classes de base réutilisables et interfaces pour votre modèle de domaine)

Le dossier de solution contient un *SeedWork* dossier. Le *SeedWork* dossier contient des classes de base personnalisées que vous pouvez utiliser comme base pour vos entités de domaine et les objets de valeur. Utilisez ces classes de base, donc vous n’avez pas de code redondant dans la classe d’objet de chaque domaine. Le dossier pour ces types de classes est appelé *SeedWork* et pas quelque chose comme *Framework*. Il est appelé *SeedWork* , car le dossier contient un sous-ensemble des classes réutilisables qui ne peut pas réellement être considérée comme une infrastructure. *Seedwork* est un terme introduit par [Michael plumes](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) déjà connues par [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) , mais vous pouvez également nommer ce dossier commun, SharedKernel, ou similaires.

Figure 9-12 montre les classes qui constituent le seedwork du modèle de domaine dans l’ordre de tri microservice. Il a quelques classes de base personnalisées comme entité, ValueObject et d’énumération, ainsi que quelques interfaces. Ces interfaces (IRepository et IUnitOfWork) informent la couche d’infrastructure sur ce qui doit être implémentée. Ces interfaces sont également utilisés par le biais d’Injection de dépendance à partir de la couche application.

![](./media/image13.PNG)

**Figure 9-12**. Un exemple de définie des classes de base de domaine modèle « seedwork » et des interfaces

Il s’agit du type de réutilisation de copier- coller de nombreux développeurs partagent entre les projets, pas un cadre formel. Vous pouvez avoir seedworks dans n’importe quel couche ou la bibliothèque. Toutefois, si l’ensemble des classes et interfaces est suffisante, vous souhaiterez créer une bibliothèque de classes unique.

## <a name="the-custom-entity-base-class"></a>La classe de base d’entité personnalisée

Le code suivant est un exemple d’une classe de base d’entité dans lequel vous pouvez placer le code qui peut être utilisé de la même façon par une entité de domaine, tels que l’ID d’entité, [opérateurs d’égalité](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), etc..

```csharp
// ENTITY FRAMEWORK CORE 1.1
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;

    public virtual int Id
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }
  
    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() \^ 31;
            // XOR for random distribution. See:
            // http://blogs.msdn.com/b/ericlippert/archive/2011/02/28/guidelines-and-rules-for-gethashcode.aspx
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }

    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null)) ? true : false;
        else
            return left.Equals(right);
    }

    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>Contrats de référentiel (interfaces) dans la couche de modèle de domaine

Contrats de référentiel sont simplement des interfaces .NET qui expriment les spécifications de contrat des espaces de stockage à utiliser pour chaque agrégat. Les référentiels eux-mêmes, avec le code d’une base de EF ou d’autres dépendances d’infrastructure et le code, ne doivent pas être implémentées dans le modèle de domaine ; les référentiels doivent uniquement implémenter les interfaces que vous définissez.

Un modèle lié à cette pratique (en plaçant les interfaces de référentiel dans la couche de modèle de domaine) est un modèle séparées par une Interface. En tant que [expliqué](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) par Martin Fowler, « utilisation séparées par Interface pour définir une interface dans un package mais l’implémenter dans un autre. De cette manière un client qui a besoin de la dépendance à l’interface peut être pas tenu au courant de l’implémentation. »

Suivant le modèle séparées par une Interface permet à la couche d’application (dans ce cas, le projet d’API Web pour le microservice) pour avoir une dépendance sur les exigences définies dans le modèle de domaine, mais pas une dépendance directe à l’infrastructure/persistance couche. En outre, vous pouvez utiliser l’Injection de dépendances pour isoler l’implémentation, qui est implémentée dans l’infrastructure / de la couche de persistance à l’aide de référentiels.

Par exemple, l’exemple suivant, avec l’interface IOrderRepository définit les opérations de la classe OrderRepository doit implémenter à la couche d’infrastructure. Dans l’implémentation actuelle de l’application, le code doit simplement ajouter l’ordre de la base de données, étant donné que les requêtes sont les suivants de fractionner que l’approche CQS et les mises à jour des commandes ne sont pas implémentées.

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
}

public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Martin Fowler. Interface séparé. ** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)


>[!div class="step-by-step"]
[Précédente] (net-core-microservice-domaine-model.md) [suivant] (implémentez-valeur objects.md)
