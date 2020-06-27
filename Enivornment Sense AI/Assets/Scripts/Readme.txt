Solving the Challenge (changes to be found already in this code).

1. You will want to record the distance travelled for each bot.  That means remembering their starting location and then recording how far they have travelled.  This is done in the Brain.cs code.

You'll need to add the properties:
	public float distanceTravelled;
	Vector3 startPosition;

Set the startPosition in Init():
       startPosition = this.transform.position;

Update startPosition in the FixedUpdate()
    if(alive)
    {
        timeAlive += Time.deltaTime;
        distanceTravelled = Vector3.Distance(this.transform.position,startPosition);
    }

Then in the PopulationManager you sort the list on the distanceTravelled instead of the timeAlive:
	List<GameObject> sortedList = population.OrderBy(o => o.GetComponent<Brain>().distanceTravelled).ToList();