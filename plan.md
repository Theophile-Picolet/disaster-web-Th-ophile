# Plan d'Optimisation EcoTraining Platform - Version Pédagogique

## Overview
Plan simplifié axé sur les principales issues à résoudre pour corriger les dysfonctionnements critiques identifiés par l'audit Lighthouse.

---

## Story 4 : Optimisation des images

**Priorité:** 🔴 P0 (Critique)  
**Ordre de réalisation:** 1️⃣ (Première à implémenter)  
**Roadmap:** M1

### Modifications prévues

#### Issue 4.1 : Compression et conversion WebP
- [ ] Réduire poids images avec ImageMagick/TinyPNG
- [ ] Convertir formats JPG/PNG → WebP (format moderne)
- [ ] Mettre en place fallback pour anciens navigateurs
- [ ] Appliquer lazy-loading (`loading="lazy"`) sur images hors viewport
- [ ] Valider absence d'artefacts visuels

### Ordre de réalisation
1. Issue 4.1 - Compression + WebP + lazy-loading (5-7 jours)

---



## Story 5 : Minification et optimisation du JavaScript

**Priorité:** 🔴 P0 (Critique)  
**Ordre de réalisation:** 2️⃣ (Deuxième à implémenter)  
**Roadmap:** M1

### Modifications prévues

#### Issue 5.1 : Minification et suppression code inutilisé
- [ ] Activer minification JavaScript dans build (webpack/TerserPlugin)
- [ ] Configurer tree-shaking pour supprimer code mort
- [ ] Identifier et supprimer dépendances inutilisées (npm audit)
- [ ] Code splitting par route avec React.lazy()
- [ ] Tester fonctionnalité complète (smoke tests)

### Ordre de réalisation
1. Issue 5.1 - Minification + tree-shaking + code splitting (5-7 jours)


## Story 6 : Nettoyage et optimisation du CSS

**Priorité:** 🟡 P2 (Moyen)  
**Ordre de réalisation:** 3️⃣ (Parallèle à Story 4-5)  
**Roadmap:** M2

### Modifications prévues

#### Issue 6.1 : Suppression CSS inutilisé et minification
- [ ] Utiliser PurgeCSS pour identifier styles non utilisés
- [ ] Supprimer CSS mort et dupliqué
- [ ] Minifier CSS en build
- [ ] Implémenter critical CSS pour above-the-fold
- [ ] Valider pas de regression visuelle

### Ordre de réalisation
1. Issue 6.1 - PurgeCSS + minification + critical CSS (3-5 jours)


## Story 7 : Mise en cache HTTP et navigateur

**Priorité:** 🟡 P2 (Moyen)  
**Ordre de réalisation:** 4️⃣ (Après JS/CSS)  
**Roadmap:** M2

### Modifications prévues

#### Issue 7.1 : Configuration du cache HTTP et Service Worker
- [ ] Configurer headers `Cache-Control` pour assets (max-age 1 année pour images, 1 mois pour JS/CSS)
- [ ] Implémenter content-based asset hashing (bundle.[hash].js)
- [ ] Créer Service Worker pour offline support et caching
- [ ] Configurer cache-first strategy pour assets statiques
- [ ] Tester cache hit rates

### Ordre de réalisation
1. Issue 7.1 - Cache HTTP + Service Worker + hashing (5-7 jours)


## Story 8 : Server-Side Rendering pour améliorer FCP/LCP

**Priorité:** 🔴 P1 (Haute)  
**Ordre de réalisation:** 5️⃣ (Après stories 4-7)  
**Roadmap:** M3

### Modifications prévues

#### Issue 8.1 : Implémentation du Server-Side Rendering
- [ ] Analyser architecture actuelle et évaluer SSR vs Static Generation
- [ ] Configurer Next.js ou custom SSR (Node.js)
- [ ] Implémenter data fetching côté serveur (getServerSideProps)
- [ ] Inliner critical CSS et déférer non-critical JS
- [ ] Configurer Lighthouse CI pour monitoring FCP/LCP

### Ordre de réalisation
1. Issue 8.1 - Setup SSR + data fetching + monitoring (7-10 jours)


## Story 9 : Correction des contrastes de couleur

**Priorité:** 🔴 P1 (Haute)  
**Ordre de réalisation:** 6️⃣ (Peut être parallèle)  
**Roadmap:** M2

### Modifications prévues

#### Issue 9.1 : Audit et correction des contrastes WCAG AA
- [ ] Scanner toutes les couleurs avec Axe DevTools et WebAIM Contrast Checker
- [ ] Identifier violations WCAG AA (ratio texte/fond < 4.5:1)
- [ ] Ajuster palette couleurs (primary, secondary, hover/focus states)
- [ ] Vérifier contraste sur textes, headings, boutons, liens
- [ ] Valider avec Lighthouse Accessibility ≥ 90

### Ordre de réalisation
1. Issue 9.1 - Audit + correction couleurs + validation (3-5 jours)


## Ordre d'exécution optimal

```
Phase 1 (Semaine 1-2): Assets & Code
├── Story 4 (Images) - 5-7 j
├── Story 5 (JS) - 5-7 j
└── Story 6 (CSS) - 3-5 j (parallèle)

Phase 2 (Semaine 2-3): Infrastructure
└── Story 7 (Cache) - 5-7 j

Phase 3 (Semaine 3-4): Performance avancée
└── Story 8 (SSR) - 7-10 j

Parallèle (Anytime): Accessibilité
└── Story 9 (Contrastes) - 3-5 j
```

**Durée totale estimée:** 4-5 semaines (avec parallélisation)

---

## Résultats attendus - Résumé

### Métriques clés

| Métrique | Avant | Après | Gain |
|----------|-------|-------|------|
| **Lighthouse Performance** | 48 | 80+ | +67% |
| **Lighthouse Accessibility** | 75 | 90+ | +20% |
| **FCP (First Contentful Paint)** | 6.9s | < 2.5s | -64% |
| **LCP (Largest Contentful Paint)** | 18.0s | < 2.5s | -86% |
| **Poids images** | 7094 KB | 2000 KB | -71% |
| **Bundle JS** | 3251 KB | 500 KB | -85% |
| **CSS** | 7093.7 KB | 500 KB | -93% |
| **Cache hit rate** | -2% | 50%+ | +2600% |

### Core Web Vitals
- ✅ FCP: < 2.5s (green)
- ✅ LCP: < 2.5s (green)
- ✅ CLS: < 0.1 (good)

### Accessibilité
- ✅ WCAG AA compliant (ratio contraste ≥ 4.5:1)
- ✅ Score Lighthouse Accessibility ≥ 90
