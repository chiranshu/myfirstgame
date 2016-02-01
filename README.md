# myfirstgame
this is the new game Where the buddy is trying to escape the enemy objects.
This game is developed in unity.
Here is the full source code of this game.
--------------------------------------------------------
#code of moving buddy.
using UnityEngine;
using System.Collections;

public class snake : MonoBehaviour
{

    // Use this for initialization
    Vector2 dir = Vector2.right;

    void Start()
    {
        InvokeRepeating("Move", 0.3f, 0.3f);
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKey(KeyCode.RightArrow))
            dir = Vector2.right;
        else if (Input.GetKey(KeyCode.DownArrow))
            dir = -Vector2.up;    // '-up' means 'down'
        else if (Input.GetKey(KeyCode.LeftArrow))
            dir = -Vector2.right; // '-right' means 'left'
        else if (Input.GetKey(KeyCode.UpArrow))
            dir = Vector2.up;
    }
    void Move()
    {
        // Move head into new direction
        transform.Translate(dir);

    }

    void OnCollisionEnter2D(Collision2D coll)
    {
        // Restart
        Destroy(gameObject);
    }
    void OnTriggerEnter2D(Collider2D coll)
    {
        Destroy(coll.gameObject);
    }
}
