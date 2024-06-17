# 1. Collider

## 1.1. Collider (thông thường)

<img height=300 src="https://github.com/minh711/unity-rigid-body-demo/assets/109033167/037b5d59-a818-4c10-a014-e2f411294866"/>

<img height=300 src="https://github.com/minh711/unity-rigid-body-demo/assets/109033167/efbe07e2-cd1a-4350-bcca-0e402dc1f32c"/>

Như vậy thì 2 object sẽ tự động đụng nhau được.

<img height=300 src="https://github.com/minh711/unity-rigid-body-demo/assets/109033167/59c5d330-0c5b-4d64-af1f-b9c68f7aec7d"/>

## 1.2. `Is Trigger` Collider

![image](https://github.com/minh711/unity-rigid-body-demo/assets/109033167/8ce07969-6c12-46c3-a4a0-93c8c699d221)

```cs
private void OnTriggerEnter2D(Collider2D collider)
{
    if (collider.CompareTag("Danger"))
    {
        Destroy(gameObject);
    }
}
```

# 2. Rigid Body

## 2.1. Body Types

<img height=300 src="https://github.com/minh711/unity-rigid-body-demo/assets/109033167/7428c104-2bd0-4da8-969e-a54dbafd4164"/>

## 2.2. Forces

### 2.2.1. `AddForce`

```cs
private Rigidbody2D rb;

private void Start()
{
    rb = GetComponent<Rigidbody2D>();
}

void Update()
{
    if (Input.GetKeyDown(KeyCode.Space))
    {
        rb.AddForce(Vector3.up * 10f, ForceMode2D.Impulse);
    }
}
```

### 2.2.2. `AddTorque`

```cs
rb.AddTorque(100f, ForceMode2D.Force);
```

## 2.3. Gun Demo

```cs
[SerializeField]
private GameObject bulletPrefab;

private void Update()
{
    if (Input.GetKeyDown(KeyCode.Space))
    {
        Shoot();
    }
}

private void Shoot()
{
    GameObject bullet = Instantiate(bulletPrefab, transform.position, transform.rotation);

    Rigidbody2D bulletRb = bullet.GetComponent<Rigidbody2D>();

    bulletRb.AddForce(transform.up * 10f, ForceMode2D.Impulse);
}
```
