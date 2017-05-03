Html:



<form class="send-mail" action="action/call"  method="POST" data-success="Exito" data-failure="Fallo">
	<input type="text" name="name">
	<input type="text" name="email">
	<input type="text" name="phone">
	<textarea name="message"></textarea>
	<input type="submit">
	<p class="return-response"></p>
</form>

Jquery:

$( ".send-mail" ).submit(function( event ) {
	event.preventDefault();
	var inputs = $(this).children("[name]");
	var data = {}
	$(inputs).each(function(i, val){
		data[$(val).attr('name')] = $(val).val();
	});
	$.ajax({
		method: $(this).attr('method'),
		url: $(this).attr('action'),
		data: data
	}).done(function(response){

	});
	$(this).children("p.return-response").html($(this).data('success'));
});
