# Repo-sync

`grammar-core` wordt als git subtree gespiegeld onder `shared/grammar-core/` in beide productrepo's.

## Enige schrijfrichting

1. Wijzig gedeelde canon in `grammar-core`.
2. Merge die PR.
3. Maak in ieder productrepo een syncbranch.
4. Voer uit:

```bash
git subtree pull --prefix=shared/grammar-core \
  https://github.com/Loumeister/grammar-core.git main --squash
```

5. Test het product en merge de sync-PR.

Wijzig nooit rechtstreeks bestanden onder `shared/grammar-core/`. Productafwijkingen horen in het lokale productcontract.

## Controle

Product-CI vergelijkt de canonieke mappen van de subtree met `grammar-core/main`. De controle schrijft niets en opent geen PR. Na een core-merge blijven product-PR's rood totdat hun subtree is bijgewerkt.

Een geïntegreerde package, plugin of monorepo is pas nodig als er werkelijk gedeelde runtimecode ontstaat.
