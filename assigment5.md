// RAG module for the Time Beetle
async function fetchWikipediaText(topic) {
  const url = `https://en.wikipedia.org/w/api.php?format=json&action=query&prop=extracts&redirects=true&explaintext&titles=${encodeURIComponent(topic)}&origin=*`;

  try {
    const response = await fetch(url);
    const data = await response.json();
    const page = Object.values(data.query.pages)[0];
    return page?.extract || "No information found.";
  } catch (error) {
    console.error("Error fetching Wikipedia data:", error);
    return null;
  }
}

// Example of using the RAG module
async function askTimeBeetle(question) {
  // Step 1: Determine the main topic from the question
  // (In a more advanced version, you could do NLP here)
  const topic = question; // For simplicity, assume question is just the topic

  // Step 2: Retrieve information
  const retrievedText = await fetchWikipediaText(topic);
  if (!retrievedText) return "Sorry, I couldn't retrieve any information.";

  // Step 3: (Placeholder) Generate answer using retrieved context
  // Here we just return the retrieved text, but in a real RAG system,
  // you'd feed this into an AI model to produce a more refined answer.
  return `Answer based on retrieved info:\n\n${retrievedText}`;
}

// Example usage
(async () => {
  const answer = await askTimeBeetle("Tim Berners-Lee");
  console.log(answer);
})();


// CHATGPT GENERARAT