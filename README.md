import net.dv8tion.jda.api.JDABuilder;
import net.dv8tion.jda.api.entities.Message;
import net.dv8tion.jda.api.events.message.MessageReceivedEvent;
import net.dv8tion.jda.api.hooks.ListenerAdapter;
import javax.security.auth.login.LoginException;

public class Main extends ListenerAdapter {
    public static void main(String[] args) throws LoginException {
        // Seu token do bot
        String token = "SEU_TOKEN_AQUI";

        JDABuilder.createDefault(token)
                  .addEventListeners(new Main())
                  .build();
    }

    @Override
    public void onMessageReceived(MessageReceivedEvent event) {
        Message msg = event.getMessage();
        String content = msg.getContentRaw();

        if (content.equalsIgnoreCase("!ping")) {
            event.getChannel().sendMessage("Pong! 🏓").queue();
        }
    }
}
