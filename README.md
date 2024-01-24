## PlayerController

Haremos que la fuerza aplicada para mover a nuestro _player_ se vea duplicada.

```cs
private void FixedUpdate() 
{
    Vector3 movement = new Vector3 (movementX, 0.0f, movementY);

    rb.AddForce((movement * speed)*2); 
}
```


## CameraController

Con este script haremos que la cámara siga el movimiento de nuestro _player_.

Hacemos esto mediante el siguiente de código:
```cs
void Start()
{
    offset = transform.position - player.transform.position; 
}
```
Establece una distancia fija entre la cámara y el _player_.

```cs
void LateUpdate()
{
    transform.position = player.transform.position + offset;  
```
Dicta que los valores de **posición** de la cámara sean los valores de **posición** de _player_ sumado a la distancia fija.

```cs
    transform.rotation = player.transform.rotation;
}
```
Hace que los valores de **rotacion** de la cámara estén ligados a nuestro _player_ haciendo que de ser modificados sus valores también lo sean modificados los de la cámara.

## CamaraCentitalController

Tenemos una cámara en plano cenital (vista desde arriba) la cuál podremos mover con las flechas del teclado.

Para su movimiento tenemos el siguiente código:

```cs
public float moveSpeed = 10f;
```
Para manejar la velocidad a la que se mueve la cámara.
```cs
void Update()
{
    if(Input.GetKey(KeyCode.UpArrow))
        transform.Translate(Vector3.up * moveSpeed * Time.deltaTime);

```
Usamos las propiedades estáticas de Vector3. En este caso '_up_' que es equivalente a Vector3(0, 1, 0).
```cs
if(Input.GetKey(KeyCode.DownArrow))
    transform.Translate(Vector3.down * moveSpeed * Time.deltaTime);
```
'_down_' que es equivalente a Vector3(0, -1, 0).
```cs
if(Input.GetKey(KeyCode.RightArrow))
    transform.Translate(Vector3.right * moveSpeed * Time.deltaTime);
```
'_right_' que es equivalente a Vector3(1, 0, 0).
```cs
if(Input.GetKey(KeyCode.LeftArrow))
    transform.Translate(Vector3.left * moveSpeed * Time.deltaTime);
}
```
'_left_' que es equivalente a Vector3(-1, 0, 0).
