# mascaramoeda

Código simples de máscara para moeda, com formaração e "R$" na frente do valor.

Seu input:

    <input type="text" name="campo_teste_name" id="campo_teste_id" class="form-control" value="">


Função:
	
	$(document).ready(function () {
	    // chamar aqui a função formatarMoeda, passando o id do input como parâmetro
	    formatarMoeda($('#campo_teste_id'));
	});

    function formatarMoeda(obj) {
        $(obj).on('keyup', function () {
            var valorDigitado = obj.val();
            valorDigitado = valorDigitado.replace('R$ ', '');
            var valorDigitado_int = parseInt(valorDigitado.replace(/[\D]+/g, ''));

            var valorFormatado = new Intl.NumberFormat('pt-BR', {
                minimumFractionDigits: 2,
                maximumFractionDigits: 2
            }).format(valorDigitado_int / 100)

            var valorFormatado = 'R$ ' + valorFormatado;
            obj.val(valorFormatado);
        });
    }
