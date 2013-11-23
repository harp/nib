# harp-nib

Nib is a Sylus library providing robust cross-browser CSS3 mixins.


## Dependencies

  - Install [NodeJS](http://nodejs.org) - _server-side JavaScript runtime_
  - Install [Harp](http://harpjs.com/docs/environment/install) - _static web server with built-in preprocessing_
  
## Install

To install nib run the following command from the root of your harp project. If you don't have a harp application, create one first.

```bash
harp install nib
```

Your Project will look something like this...

```
  myproject/            <-- your project root (or public dir if in framework-mode)
    |- components/      <-- harp puts components here
    |   +- harp-nib/    <-- where this lib gets installed
    |         ...
    |- main.styl        <-- your css file you reference 
    +- index.jade       <-- your home page (as they used to call it)

```

From within a **.styl** file in your project you can then **@import** nib, or a portion of nib:

##### main.styl

```styl
@import "components/harp-nib/nib";
@import "components/harp-nib/nib/iconic";
```

## Resources

* [Harp documentation](http://harpjs.com/docs/)
* [Stylus documentation](http://learnboost.github.io/stylus/)
* [Nib documentation](http://visionmedia.github.com/nib/)

## License

This component is [Nib](https://github.com/visionmedia/nib), which is MIT Licensed.
