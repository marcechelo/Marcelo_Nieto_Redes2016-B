package ec.edu.epn.redes.cs.tcp;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.ServerSocket;
import java.net.Socket;
import java.util.StringTokenizer;

/**
 * A TCP server that runs on port 9090.  When a client connects, it
 * sends the client a message, then closes the
 * connection with that client.  Arguably just about the simplest
 * server you can write.
 */
public class ServerTCP {

	private static int PORT = 9090;
	
     /**
     * Runs the server.
     */
    public static void main(String[] args) throws IOException {
        
    	ServerSocket serverSocket = new ServerSocket(PORT);
        System.out.println("Server listening on port "+PORT);
        int suma=0;
        
        try {
            while (true) {
                Socket socket = serverSocket.accept();
                //Se crea la variable inputStream para leer el mensaje enviado por el cliente
                InputStreamReader inputStream = new InputStreamReader(socket.getInputStream());
                try {
                	
                	//Se crea el bufferReader que nos permitira extraer el String enviado por el cliente
                	//Una vez extraido el String se separan los valores con el StringTokenizer y se suman
                	//los valores para enviar la suma al cliente.
            		BufferedReader input = new BufferedReader(inputStream);
            		String answer = input.readLine();
            		StringTokenizer st = new StringTokenizer(answer	, ",");
            		while (st.hasMoreTokens()) {
						suma+=Integer.parseInt(st.nextToken());
					}
                    PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
                    out.println(suma); 
                } finally {
                    socket.close();
                }
            }
        }
        finally {
        	serverSocket.close();
        }
    }
	
}
