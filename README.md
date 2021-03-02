

#usage
1)Read 10th character of the Web view text.
```xml    
 Reader reader = new InputStreamReader(is, "UTF-8");

                    int ch = 0;
                    for (int i=0; i < 10; i++) {
                        ch = reader.read();
                        if (ch == -1)
                            return "error:\nEmpty";
                    }

                    return "10th character in the web page text is '" + (char)ch;
    ...
```
2)Read Every 10th character of the Web view text.
```xml    
                    int ch;
                    while ((ch = reader.read()) != -1 ) {
                        if (i > 0 && i % 10 == 0) {
                            sb.append((char) ch);
                            if (j > 0 && j % 10 == 0) sb.append(' ');
                            j++;
                        }
                        i++;
                    }
                    sb.append("'");
    ...
```
3)Read the sentence and split the word with space of the Web view text.
```xml    
                    Map<String, Integer> wc = new TreeMap<>();
                    String line = null;
                    while( (line = br.readLine())!= null ){
                        String [] tokens = line.split("[\\s\\d~`!@#\\$%\\^&\\*\\(\\)\\-\\+\\[\\]\\{\\}\'\"\\\\|/\\?,\\.;:]+");
                        for (String token : tokens) {
                            if (token.equals("")) continue;
                            token = token.toLowerCase();
                            int n = wc.containsKey(token)? wc.get(token) : 0;
                            n++;
                            wc.put(token, n);
                        }
                    }

                    StringBuilder sb = new StringBuilder();
                    sb.append("result:\n");
                    for (Map.Entry<String, Integer> e : wc.entrySet()) {
                        sb.append(e.getKey())
                                .append(" : ")
                                .append(e.getValue())
                                .append("\n");
                    }
    ...
```
