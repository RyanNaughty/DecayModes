DecayModes
==========
	public ArrayList<ArrayList<String>> getDecayModes(ParticleNodeInterface node) 
	{
		
		ArrayList<ArrayList<String>> all_decay_modes = new ArrayList< ArrayList<String>>();
		
		
		if  (node.getLNode() == null || node.getRNode() == null)
		{
			return(all_decay_modes);
		}

		ArrayList<String> combine = new ArrayList<String>();

		combine.add(node.getLNode().getName());
		combine.add(node.getRNode().getName());
		
		all_decay_modes.add(combine);

		
		ArrayList<ArrayList<String>> lNodeDecays = new ArrayList< ArrayList<String>>();
		if  (node.getLNode() != null) lNodeDecays = getDecayModes(node.getLNode());

		ArrayList<ArrayList<String>> rNodeDecays = new ArrayList< ArrayList<String>>();
		if  (node.getRNode() != null) rNodeDecays = getDecayModes(node.getRNode());

		
			 
		for(int i = 0; i < lNodeDecays.size();i++)
		{

			ArrayList<String> element = lNodeDecays.get(i);

			combine = new ArrayList<String>();
			combine.add(node.getRNode().getName());

			for(int j = 0; j < element.size();j++)
			{
				combine.add(element.get(j));
			
			}
			all_decay_modes.add(combine);
			
			
		}

		for(int i = 0; i < rNodeDecays.size();i++)
		{

			ArrayList<String> element = rNodeDecays.get(i);

			combine = new ArrayList<String>();
			combine.add(node.getLNode().getName());

			for(int j = 0; j < element.size();j++)
			{
				combine.add(element.get(j));
			
			}

			all_decay_modes.add(combine);
			
			
		}

		
		for(int i = 0; i < lNodeDecays.size();i++)
		{
			
			for(int j = 0; j < rNodeDecays.size();j++)
			{
				
				ArrayList<String> elementL = lNodeDecays.get(i);

				ArrayList<String> elementR = rNodeDecays.get(j);

				combine = new ArrayList<String>();

				for(int t = 0; t < elementL.size();t++)
				{
					combine.add(elementL.get(t) );
				}
				
				for(int u = 0; u < elementR.size();u++)
				{
					combine.add(elementR.get(u) );
				}
				
				all_decay_modes.add(combine);
				
			}

		}

		return(all_decay_modes);
		
	}
