# esbuild-plugin-lightningcss-modules

Yet another css modules plugin for esbuild? Pleaso no?

Yes sorry, i know there are a few implementions already out there:

- @asn.aeb/esbuild-css-modules-plugin
- esbuild-css-modules-plugin
- esbuild-plugin-css-modules
- esbuild-style-plugin
- esbuild-plugin-simple-css-modules

The problem is, they dindt suit my usecase as i needed support for css modules composes feature https://github.com/css-modules/css-modules#dependencies
`composes: mixin from './mixin.module.css';` 

The above implementations mostly rely on `post-cssmodules` and thus dont sucessfully support composition from dependencies as they suffer from this problem: https://github.com/g45t345rt/esbuild-style-plugin/issues/16 (The webpack css modules plugin goes to great lenghts to archieve it successfully)

With one exception: `esbuild-css-modules-plugin`, this plugin uses also lightningcss as its core, but doesnt support composes yet and due to a more complex inject feature it is a bit more complex. I discussed with the maintainer if we would want to merge our two packages but due to limited time and different usecases (https://github.com/indooorsman/esbuild-css-modules-plugin/issues/53) im here to present my super simple implemented css module plugin for esbuild.

The plugin is already tested (on linux and mac) and used to build the following bigger project https://github.com/neos/neos-ui with around 100 css modules - it is inlined in the project though to reduce dependencies and maintaining burdens for now.