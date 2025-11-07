<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>Ejemplo PHP if/for/while</title>
  <style>
    body{font-family:Arial;padding:20px}
    .box{background:#f7f7f7;padding:12px;border-radius:6px;max-width:480px}
    input[type=number]{width:80px}
    .result{margin-top:10px;padding:8px;border-radius:4px}
  </style>
</head>
<body>
  <div class="box">
    <h3>Ingresa un número</h3>
    <form method="post">
      <input type="number" name="n" required min="1" value="<?php echo isset($_POST['n'])?htmlspecialchars($_POST['n']):''; ?>">
      <button type="submit">Enviar</button>
    </form>

<?php
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['n'])) {
    $n = intval($_POST['n']);

    // IF: par o impar
    if ($n % 2 === 0) {
        echo "<div class='result'>El número $n es <strong>par</strong>.</div>";
    } else {
        echo "<div class='result'>El número $n es <strong>impar</strong>.</div>";
    }

    // FOR: suma 1..n
    $suma = 0;
    for ($i = 1; $i <= $n; $i++) {
        $suma += $i;
    }
    echo "<div class='result'>Suma de 1 a $n = $suma</div>";

    // WHILE: cuenta regresiva
    echo "<div class='result'>Cuenta regresiva: ";
    $k = $n;
    while ($k >= 1) {
        echo $k;
        if ($k > 1) echo " - ";
        $k--;
    }
    echo "</div>";
}
?>
  </div>
</body>
</html>
