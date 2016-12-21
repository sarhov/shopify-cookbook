<script>
	Checkout.$('[name="checkout[shipping_address][phone]"]').on("keypress", function(event) {
	var numbersOnly = /[0-9]/g;
	var key = String.fromCharCode(event.which);
	if (event.keyCode == 8 || event.keyCode == 37 || event.keyCode == 39 || numbersOnly.test(key)) {
		if(charLength >= maxLength){
			return false;
		}
		else{
			return true;
		}
	}
	return false;
});
Checkout.$('[name="checkout[shipping_address][phone]"]').on("paste",function(e){
	e.preventDefault();
});

Checkout.$('[name="checkout[shipping_address][phone]"]').on("keyup", function(event) {
	charLength = Checkout.$(this).val().length;
});
</script>
