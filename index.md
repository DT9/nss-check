<style>
html,
body {
  margin: 0;
  padding: 0;
}

html,
body {
  width: 100%;
  height: 100%;
  overflow: hidden;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  outline: none;
}

body {
  background: -webkit-linear-gradient(top, #639EDB, #0668CF) no-repeat;
  background: linear-gradient(to bottom, #639EDB, #0668CF) no-repeat;
  font-family: 'Arimo', sans-serif;
  background-size: 100%;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
}

p {
  text-align: center;
  color: #ffffff;
  font-size: 13px;
}

a:hover, a:visited, a:hover, a:link {
  color: rgba(255, 255, 255, 0.6);
}

.register {
  margin: 0 auto 0;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
}

.field {
  width: 385px;
  height: 70px;
  position: relative;
}
.field input {
  width: 100%;
  border-radius: 6px;
  height: 70px;
  border: 0;
  padding: 10px;
  padding: 20px 0 0 16px;
  font-size: 0;
  background: #1566BB;
  -webkit-transition: background .3s ease;
  transition: background .3s ease;
  color: #ffffff;
}
.field input:focus {
  background: #065CB7;
  font-size: 23px;
}
.field input:focus::-moz-selection {
  background: rgba(188, 232, 255, 0.5);
}
.field input:focus::selection {
  background: rgba(188, 232, 255, 0.5);
}
.field input.active {
  background: #065CB7;
  font-size: 23px;
}
.field input,
.field button {
  position: absolute;
  height: 70px;
}
.field button {
  background: rgba(0, 0, 0, 0.3);
  right: 0;
  border: 0;
  width: 115px;
  border-radius: 6px;
  font-size: 22px;
  cursor: pointer;
  -webkit-transition: width .3s ease, background .3s ease, opacity .3s ease;
  transition: width .3s ease, background .3s ease, opacity .3s ease;
  opacity: 0;
  color: #065CB7;
  text-transform: uppercae;
  pointer-events: none;
}
.field button.active {
  color: #ffffff;
  background: #639EDB;
  opacity: 1;
  pointer-events: auto;
}
.field button.active:hover {
  background: #5E99D6;
}
.field button.full {
  width: 100%;
}
.field input:focus + label {
  font-size: 19px;
  -webkit-transform: translate(16px, 11px);
          transform: translate(16px, 11px);
  color: rgba(255, 255, 255, 0.7);
}
.field label {
  position: absolute;
  color: white;
  -webkit-transform: translate(16px, 20px);
          transform: translate(16px, 20px);
  -webkit-transition: font-size .3s ease, color .3s .1s ease, -webkit-transform .3s ease;
  transition: font-size .3s ease, color .3s .1s ease, -webkit-transform .3s ease;
  transition: transform .3s ease, font-size .3s ease, color .3s .1s ease;
  transition: transform .3s ease, font-size .3s ease, color .3s .1s ease, -webkit-transform .3s ease;
  font-size: 28px;
}
.field label.active {
  font-size: 19px;
  -webkit-transform: translate(16px, 11px);
          transform: translate(16px, 11px);
  color: rgba(255, 255, 255, 0.7);
}
.field input:focus + label + button {
  opacity: 1;
}
</style>
<div class="register">
  <div class="field">
    <input id="register" maxlength="21" type="text" /><label for="register"><span>Email Address</span></label><button>OK</button>
  </div>
</div>
<p>
  Inspired by <a href="https://dribbble.com/shots/2359423-Daily-UI-026-Subscribe" target="_blank">Derek Torsani</a>
</p>
<script type="text/javascript">
var $form = $('.register');

function validateEmail(email) {
	var regex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
	return regex.test(email);
};

$form.on('keyup', 'input', function (e) {
	var $this = $(this),
	    $input = $this.val();
	if ($input.length > 0) {
		$form.find('label').addClass('active');
		if (validateEmail($input)) {
			$form.find('button').addClass('active');
			console.log(e);
			if (e.which === 13) {
				$form.find('button').click();
				$this.blur();
			}
		} else {
			$form.find('button').removeClass('active');
		}
		$(this).addClass('active');
	} else {
		$form.find('label').removeClass('active');
		$form.find('button').removeClass('active');
		$(this).removeClass('active');
	}
});

$form.on('click', 'button.active', function (e) {
	e.preventDefault;
	var $this = $(this);
	$(this).addClass('full');
	$(this).html('Thanks!');

	setTimeout(function () {
		$form.find('input').val('').removeClass('active');
		$form.find('label').removeClass('active');
		$this.removeClass('full active');
		$this.html('OK');
	}, 1200);
});
</script>