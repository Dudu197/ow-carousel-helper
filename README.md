# ow-carousel-helper

$(".owl-carousel").each(function() {
		itens = $(this).data("itens");
		dots = $(this).data("dots");
		margin = $(this).data("margin");
		center = $(this).data("center");
		soma = 0;
		loop = $(this).data("loop");
		if(typeof dots === typeof undefined && dots === false){
			dots = false;
		}
		if(typeof margin === typeof undefined && margin !== false){
			margin = 0;
		}
		if(typeof center === typeof undefined && center !== false){
			center = true;
		}
		if(typeof loop === typeof undefined && loop !== false){
			loop = true;
		}
		if(typeof itens === typeof undefined && itens === false){
			itens = 5;
			desktop = Math.round(itens/2);
		}else{
			if(itens instanceof Array){
				if(itens.length === 3){
					desktop = itens[1];
					mobile = itens[2];
					itens = itens[0];
				}
			}else{
				desktop = Math.round(itens/2);
				mobile = Math.round(itens/3);
			}
			soma = parseInt((itens/2) + "");
			$(this).data("somar", soma);
		}
		$(this).owlCarousel({
		  center: center,
		  items : itens,
		  margin: margin,
		  loop: loop,
		  dots: dots,
		  responsiveClass:true,
		  responsive:{
			0:{
			    items:mobile
			},
			768:{
			    items:desktop
			},
			1000:{
			    items: itens,
		    }
		   }
		});
