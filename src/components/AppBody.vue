<template>
    <div class="body">
        <h1>
            <a href="" class="typewrite" data-period="2000" :data-type=texts>
                <span class="wrap"></span>
            </a>
        </h1>
    </div>
</template>

<script>
export default {
    mounted() {
        // console.log('haha')
        this.Typing()
    },
    data:()=>({
        count: 0,
        textNow : '',
        texts: [ "Hello World !" ," My name is Hafizh Abdillahh.","Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."]
    }),
    methods: {
        Typing: function () {
            console.log('ini jalan kok ')
            var elements = document.getElementsByClassName('typewrite');
                for (var i=0; i<elements.length; i++) {
                    var toRotate = elements[i].getAttribute('data-type');
                    var period = elements[i].getAttribute('data-period');
                    console.log(toRotate,'====')
                    if (toRotate) {
                    this.TxtType(elements[i], toRotate, period);
                    }
                }
        // INJECT CSS
        var css = document.createElement("style");
        css.type = "text/css";
        css.innerHTML = ".typewrite > .wrap { border-right: 0.08em solid #fff}";
        document.body.appendChild(css);
        },
        TxtType : function(el,toRotate,period) {
            console.log('masuk')
            this.toRotate = toRotate;
            this.el = el;
            this.loopNum = 0;
            this.period = parseInt(period, 10) || 2000;
            this.txt = '';
            this.tick();
            this.isDeleting = false;
        },
        tick :  function() {
            // console.log(this.isDeleting)
            // console.log(this.toRotate.p,'--')
            var i = this.loopNum % this.toRotate.length;
                var fullTxt = this.toRotate.split(',')[i];
                this.textNow = fullTxt
                // console.log(this.textNow,'!!!')
                if (this.isDeleting) {
                    this.txt = fullTxt.substring(0, this.txt.length - 1);
                    } else {
                    this.txt = fullTxt.substring(0, this.txt.length + 1);
                }

                this.el.innerHTML = '<span class="wrap">'+this.txt+'</span>';

                var that = this;
                var delta = 200 - Math.random() * 100;

                if (this.isDeleting) { delta /= 2; }
                
                if (!this.isDeleting && this.txt === fullTxt) {
                    delta = this.period;
                    this.isDeleting = true;
                } else if (this.isDeleting && this.txt === '') {
                    this.isDeleting = false;
                    this.loopNum++;
                    delta = 500;
                }

                setTimeout(function() {
                that.tick();
                }, 150);
        }
    },
    watch: {
        textNow: function(val) {
            // console.log(this.count,'=======!!!=======',this.textNow,'==',this.texts[this.texts.length-1])
            // console.log(this.texts.length)
            if(this.count<this.texts.length) {
                console.log('masuk ke count up')
                this.count++
            } else if(this.count>=this.texts.length && this.textNow == undefined) {
                console.log('masuk ke count down')
                this.count = 0;
                this.Typing()
            }
        }
        
        }
            

}
</script>

<style>
    .body {
  background-color:#ce3635;
  text-align: center;
  color:#fff;
  padding-top:10em;
}

* { color:#fff; text-decoration: none;}
</style>
