public interface PaymentProcessor {
    void processPayment(double amount);
}


public class CreditCardProcessor implements PaymentProcessor {
    public void processPayment(double amount) {
        // Lógica para procesar pagos con tarjeta de crédito
        System.out.println("Procesando pago con tarjeta de crédito: " + amount);
    }
}

public class PayPalProcessor implements PaymentProcessor {
    public void processPayment(double amount) {
        // Lógica para procesar pagos con PayPal
        System.out.println("Procesando pago con PayPal: " + amount);
    }
}

public class OrderService {
    private PaymentProcessor processor;

    public OrderService(PaymentProcessor processor) {
        this.processor = processor;
    }

    public void processOrder(double amount) {
        processor.processPayment(amount);
    }
}


public class Main {
    public static void main(String[] args) {
        PaymentProcessor creditCardProcessor = new CreditCardProcessor();
        OrderService orderService = new OrderService(creditCardProcessor);
        orderService.processOrder(100.0);  // Procesando pago con tarjeta de crédito: 100.0

        PaymentProcessor paypalProcessor = new PayPalProcessor();
        orderService = new OrderService(paypalProcessor);
        orderService.processOrder(200.0);  // Procesando pago con PayPal: 200.0
    }
}
![WhatsApp Image 2024-10-10 at 5 55 13 PM](https://github.com/user-attachments/assets/e3430b03-2884-4f3e-b967-fcbc7fa1bb1c)

